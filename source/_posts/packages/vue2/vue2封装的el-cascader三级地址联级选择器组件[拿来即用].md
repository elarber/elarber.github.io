---
title: vue2封装的el-cascader三级地址联级选择器组件[拿来即用]

index_img: https://download.csdn.net/download/qq_42618566/87377829
lazyload: true
categories:
- vue2
- 拿来主义
tags:
- vue2
- elementUI


---











![](https://img-blog.csdnimg.cn/fe9f2f0faf604f5196d7faf725d354da.png)

#### 组件：
```javascript
<template>
  <el-cascader
    filterable
    clearable
    v-model="address"
    :options="options"
    :props="{ expandTrigger: 'hover', value: 'code', label: 'name', ...props }"
    :size="size"
    :disabled="disabled"
    :placeholder="placeholder"
    @focus="focus"
    @visible-change="visibleChange"
    @input="change"
    @change="change"
  ></el-cascader>
</template>

<script>
/**
 * @author        全易
 * @time          2023-01-09 17:30:41  星期一
 * @description   地址联级选择器
 **/
import address from "@/assets/json/address.json"

export default {
  name: "address-cascader",
  props: {
    // 动画流动lable
    animatLable: {
      type: Boolean,
      default: false,
    },
    // 父组件v-model绑定的值
    value: {
      type: Array,
    },
    size: {
      type: String,
      default: "medium",
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    props: {
      type: Object,
    },
    placeholder: {
      type: String,
      default: "",
    },
  },
  data() {
    return {
      address,
      options: [],
    };
  },
  created() {
    this.getData();
  },
  watch: {
    // 实时联动父组件传来的值
    value(now, old) {
      console.log(now);
      this.address = now || [];
    },
  },
  methods: {
  getData() {
      fetch(`${process.env.VUE_APP_ORIGIN}/addrTree/address2021.json`)
        .then((res) => {
          return res.json();
        })
        .then((res) => {
          // console.log("地址数据：", res);
          this.options = res;
        });
    },
    focus() {
      this.$emit("focus");
    },
    visibleChange(status) {
      console.log(status);
      this.$emit("visible-change", status);
    },
    // 绑定v-model 实时联动父组件传来的值
    change(value) {
      this.$emit("change", value);
    },
  },
};
</script>

<style lang="less" scoped>
</style>
```
> 获取[树形数据`address.json`](https://download.csdn.net/download/qq_42618566/87377829)
> [https://gitee.com/wonderlande/geo-data/blob/master/index.json](https://gitee.com/wonderlande/geo-data/blob/master/index.json)


