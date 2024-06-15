---
title: Vue2 使用事件跳转页面

index_img: https://img-blog.csdnimg.cn/20200330181521694.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





# 给标签添加点击事件：
![Vue 使用事件跳转页面](https://img-blog.csdnimg.cn/202003301758291.png)


# get传参：
```javascript
this.$router.push({
	path:"",
	query:{
	
	}
})
```

![Vue 使用事件跳转页面](https://img-blog.csdnimg.cn/20200330180356548.png)

# 传参结果
![Vue 使用事件跳转页面](https://img-blog.csdnimg.cn/20200330180533765.png#pic_center)



# 参数接收
```javascript
this.$route
```
![Vue 使用事件跳转页面](https://img-blog.csdnimg.cn/20200330181400537.png)

结果如图：
![Vue 使用事件跳转页面](https://img-blog.csdnimg.cn/20200330181521694.png)


# post传参：
```javascript
this.$router.push({
  name:"",
  parmas:{

  }
})
```

# 接收：

```javascript
this.$route
```
