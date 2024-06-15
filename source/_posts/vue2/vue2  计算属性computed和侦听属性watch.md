---
title: vue2计算属性:computed和侦听属性:watch

index_img: https://img-blog.csdnimg.cn/20200310140036470.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





#### computed计算属性：
直接在视图层逻辑运算：
```html
<template>
  <view class="test">
    {{ text.split('').reverse().join('') }}
  </view>
</template>

<script>
  export default {
    name: 'test',
    data () {
      return {
        text:'1234'
      }
    }
  }
</script>

<style lang="less" scoped>
  
</style>
```
页面输出：
![vue  computed和watch](https://img-blog.csdnimg.cn/20200310140036470.png)

使用computed计算：

```javascript
<template>
  <view class="test">
    {{ yayayayay}}
  </view>
</template>

<script>
  export default {
    name: 'test',
    data () {
      return {
        text:'1234'
      }
    },
	computed:{
		yayayayay:function(){
			return this.text.split('').reverse().join('');
		}
	}
  }
</script>

<style lang="less" scoped>
  
</style>
```
页面输出：
![vue  computed和watch](https://img-blog.csdnimg.cn/2020031014013510.png)
**注意：** computed属性里不能写箭头函数，就要些标准的函数表达式
computed属性里的`yayayayay`函数计算完要`return`，那么yayayayay就可以直接在视图层进行渲染了

既然结果都一样，为什么要使用computed计算呢？
当我们的表达式中放入太多逻辑，就会导致模板语法越来越复杂，不利于理解，难于维护。视图层就是用于渲染数据的，要做逻辑运算，有专门的地方


---


#### watch监听属性：
检测变量发生变化，触发watch属性。用于监听某个变量发生变化后要实行的操作。被监听的对象会返回两个参数，**一个是新值，一个是旧值：**

```html
<template>
  <view class="test">
		<view>{{ text }}</view>
    <view>{{ textt }}</view>
		<!-- <view>{{ food.name }}</view> -->
  </view>
</template>

<script>
  export default {
    name: 'test',
    onShow() {
			// 两秒钟后改变变量值
    	setTimeout(()=>{
				this.text="333333";
				// this.food.name = '棒棒糖'
			},2000)
    },
    data () {
      return {
        text:'1234',
				/* food: {
						id: 1,
						name: '冰激凌'
				} */
      }
    },
		computed:{
			textt:function(){
				return this.text.split('').reverse().join('');
			}
		},
		watch:{
			// 监听text
			text:function(now,old){  //被监听的对象会返回两个参数，一个是变化后的值，一个是变化前的值
			// 打印看看
				console.log("新值："+now);
				console.log("旧值："+old);
				/* 
				
				在此可做些逻辑 
				 
				 */
			},
		/* 	food: {
				handler(newVal, oldVal) {// food的每个属性值发生变化就会调用handler()
						console.log('oldVal:', oldVal)
						console.log('newVal:', newVal)
				},
				immediate: true,// 立即处理 进入页面就触发
				deep: true// 深度监听 属性的变化
			},
			
			'food.name'(newVal, oldVal) { // 第二种方式：监听对象的某个属性，被监听的属性值发生变化就会执行函数
					console.log('oldVal:', oldVal)   // 冰激凌
					console.log('newVal:', newVal)   // 棒棒糖
			} */
		}
  }
</script>

<style lang="less" scoped>
  
</style>
```
打印结果如图：
![vue  computed和watch](https://img-blog.csdnimg.cn/20200310145142725.png)
