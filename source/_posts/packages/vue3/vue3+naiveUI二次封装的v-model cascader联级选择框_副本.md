---
title: vue3+naiveUI二次封装的v-model 联动输入框

index_img: https://img-blog.csdnimg.cn/direct/0443fc52c2e44f148f374aae1398101e.gif
lazyload: true
categories:
- vue3
- 拿来主义

tags:
- vue3
- 拿来主义


---









根据[官网说明](https://cn.vuejs.org/guide/components/v-model.html)使用

![请添加图片描述](https://img-blog.csdnimg.cn/direct/0443fc52c2e44f148f374aae1398101e.gif)



# 源码

```html
<template>
  <div class="clw-input pt-3">
    <n-input
      ref="input"
      :value="modelValue"
      :type="type"
      :title="title"
      clearable
      :disabled="disabled"
      :size="size"
      placeholder=""
      @focus="$emit('focus')"
      @blur="blur"
      @input="input"
      @change="change"
    />
    <label class="z-1 text-warmgray" :style="style">{{ placeholder }}</label>
  </div>
</template>

<script>
/**
 * @author        全易
 * @time          2022-10-11 13:08:46  星期二
 * @description   自定义输入框组件
 **/

export default {
  name: 'ClwInput',
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
    size: {
      type: String,
      default: 'medium',
    },
    disabled: {
      type: Boolean,
    },
    labelBG: {
      type: String,
      default: '#ffffff',
    },
    labelColor: {
      type: String,
      default: '#19aa8d',
    },
    type: {
      type: String,
      default: '',
    },
  },
  emits: ['focus', 'blur', 'change', 'update:modelValue'],
  data() {
    return {
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
      handler() {
        this.resetStyle()
      },
    },
  },
  mounted() {
    this.inputHeight = this.$refs.input.$el.offsetHeight
    this.resetStyle()
  },
  methods: {
    blur() {
      this.resetStyle()
      this.$emit('blur')
    },
    input(val) {
      this.resetStyle()
      this.$emit('update:modelValue', val)
    },
    change(val) {
      this.$emit('change', val)
    },
    resetStyle() {
      if (this.modelValue) {
        this.style = {
          transform: `translateY(${-(this.inputHeight / 2)}px)`,
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
.clw-input {
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
<clw-input
  v-model="queryForm.propertyNo"
   placeholder="物业编号"
   @keydown.enter="getData"
 ></clw-input>
```


