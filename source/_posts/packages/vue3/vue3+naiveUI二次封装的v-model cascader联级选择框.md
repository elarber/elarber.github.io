---
title: vue3+naiveUI二次封装的v-model cascader联级选择框

index_img: https://img-blog.csdnimg.cn/direct/004bc4191963474bb322e9bf0019828e.gif
lazyload: true
categories:
- vue3
- 拿来主义

tags:
- vue3
- 拿来主义


---









[组件 v-model](https://cn.vuejs.org/guide/components/v-model.html)

![请添加图片描述](https://img-blog.csdnimg.cn/direct/004bc4191963474bb322e9bf0019828e.gif)




# 源码

```html
<template>
  <div class="clw-cascader pt-3">
    <n-cascader
      ref="cascader"
      :value="value"
      :title="title"
      filterable
      clearable
      :check-strategy="checkStrategy"
      :label-field="labelField"
      :value-field="valueField"
      :options="options"
      :size="size"
      :disabled="disabled"
      placeholder=""
      @change="change"
      @focus="focus"
      @blur="blur"
      @input="input"
    ></n-cascader>
    <label class="z-1 text-warmgray" :style="style">{{ placeholder }}</label>
  </div>
</template>

<script>
/**
 * @author        全易
 * @time          2022-10-11 13:08:46  星期二
 * @description   自定义联级选择器
 **/

export default {
  name: 'ClwCascader',
  props: {
    placeholder: {
      type: String,
      default: '',
    },
    // 父组件v-model绑定的值
    modelValue: {
      type: String,
      default: '',
    },
    options: {
      type: Array,
      default() {
        return []
      },
    },
    labelField: {
      type: String,
      default: '',
    },
    valueField: {
      type: String,
      default: '',
    },
    checkStrategy: {
      type: String,
      default: 'child',
    },
    size: {
      type: String,
      default: 'medium',
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    labelBG: {
      type: String,
      default: '#ffffff',
    },
    labelColor: {
      type: String,
      default: '#19aa8d',
    },
  },
  emits: ['focus', 'blur', 'input', 'change', 'update:modelValue'],
  data() {
    return {
      value: '',
      inputHeight: null,
      style: {},
    }
  },
  computed: {
    title() {
      return `${this.placeholder}：${this.modelValue}`
    },
  },
  watch: {
    modelValue: {
      deep: true,
      handler(now) {
        this.value = now[now.length - 1] || ''
        this.resetStyle()
      },
    },
  },
  mounted() {
    this.inputHeight = this.$refs.cascader.$el.offsetHeight
    this.resetStyle()
  },
  methods: {
    focus() {
      this.$emit('focus')
    },
    blur() {
      this.resetStyle()
      this.$emit('blur')
    },
    input(val) {
      this.$emit('input', val)
    },
    change(value, option, all) {
      // console.log(value)
      // console.log(option)
      // console.log(all)
      this.$emit('update:modelValue', value)
      if (all) {
        this.$emit(
          'change',
          all.map((item) => {
            return item.code
          })
        )
      } else {
        this.$emit('change', [])
      }
      this.resetStyle()
    },
    resetStyle() {
      if (this.value) {
        this.style = {
          transform: `translateY(${-(this.inputHeight * 1.47)}px)`,
          color: `${this.labelColor} !important`,
          'background-color': this.labelBG,
          padding: '0 10px',
        }
      } else {
        this.style = {
          bottom: `${this.inputHeight * 0.18}px`,
        }
      }
    },
  },
}
</script>

<style lang="scss" scoped>
.clw-cascader {
  position: relative;

  label {
    position: absolute;
    left: 15px;
    pointer-events: none;
    transition: all 0.3s ease;
  }
}
</style>

```

# 使用

```html
<clw-cascader
  v-model="queryForm.address3"
   label-field="name"
   value-field="code"
   animat-lable
   placeholder="地址筛选"
 />
```


