---
title: css 可以计算的属性值：calc()函数

index_img: https://img-blog.csdnimg.cn/20200122174027894.png
lazyload: true
categories:
- css


tags:
- css

---




> `calc()` 函数使我们可以在属性值中执行 加、减、乘、除 等数学计算的操作。


示例：

```css
  .div{
	  width: 16.666666667%;
    }
```

  
==就可以写成：==

```css
.div{
	 width: calc(100% / 6);
}
```


#### 1. 语法：
`calc(除数 运算符 被除数)` ，三个参数间一定要**空一格**！


#### 2. 特性
1. 用来计算；
2. 可以嵌套
例如：
		![css 可以计算的属性值：calc()函数](https://img-blog.csdnimg.cn/20200122173901520.png)
		也可以简写成：
		![css 可以计算的属性值：calc()函数](https://img-blog.csdnimg.cn/20200122173804214.png)
		
		
---

实例：
![css 可以计算的属性值：calc()函数](https://img-blog.csdnimg.cn/20200122174027894.png)

