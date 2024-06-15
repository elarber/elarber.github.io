---
title: vue引入高德地图

index_img: https://img-blog.csdnimg.cn/20201220120116110.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





#### 1. 官方获取key：[https://console.amap.com/dev/key/app](https://console.amap.com/dev/key/app)


![](https://img-blog.csdnimg.cn/20201220120116110.png)

#### 2. index.html引入

```html
<script type="text/javascript" src="https://webapi.amap.com/maps?v=1.4.15&key=你申请的key"></script> 
```

![](https://img-blog.csdnimg.cn/20201220120305229.png)
#### 3.配置`build/webpack.base.conf.js`：

```javascript
externals: {
    'AMap': 'AMap'
  },
```
![](https://img-blog.csdnimg.cn/20201220120534491.png)

#### 重启项目，使用
我封装成组件了
```html
<template>
  <el-dialog
    width="65%"
    :append-to-body="true"
    :modal-append-to-body="false"
    title="地图"
    :visible="show"
    :before-close="close"
  >
    <div>
      <div class="search">
        <el-input id="tipinput" v-model="searchText"></el-input>
      </div>
      <div id="amap"></div>
    </div>
    <span slot="footer" class="dialog-footer">
      <el-button @click="close">取 消</el-button>
      <el-button type="primary" @click="ok">确 定</el-button>
    </span>
  </el-dialog>
</template>

<script>
/**
 * @author        全易
 * @time          2020-12-20 10:18:12  星期天
 * @description   高德地图
 */

export default {
  name: "Amap",
  props: {
    show: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      map: null,
      searchText: "",
      data: {},
    };
  },
  mounted() {
    console.log("高德地图：", AMap);
  },
  watch: {
    show(now, old) {
      if (now) {
        this.$nextTick(() => {
          this.amap();
        });
      }
    },
  },
  methods: {
    // 初始化地图
    amap() {
      this.map = new AMap.Map("amap", {
        resizeEnable: true,
        zoom: 11,
        center: [116.397428, 39.90923],
      });

      this.map.plugin(["AMap.ToolBar"], function () {
        this.map.addControl(new AMap.ToolBar());
      });
      if (location.href.indexOf("&guide=1") !== -1) {
        this.map.setStatus({ scrollWheel: false });
      }

      this.click();

      //输入提示
      var auto = new AMap.Autocomplete({
        input: "tipinput",
      });
    },
    // 点击地图
    click() {
      const that = this;
      this.map.on("click", function (e) {
        console.log(e);
        that.data = e;
        // console.log(e.lnglat.getLng() + "," + e.lnglat.getLat());
      });
    },
    // 关闭地图面板
    close() {
      this.$emit("close", false);
    },
    // 确定
    ok() {
      this.$emit("ok", this.data);
      this.close();
    },
  },
};
</script>

<style lang="less" scoped>
#amap {
  width: 100%;
  height: 60vh;
}
</style>
```
