---
title: vue 动态组件：component标签

index_img: https://quanyi.blog.csdn.net/article/details/113755417
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





> ` <component :is="组件" />`

# 引入：
```javascript
import NewUsers from "./panels/new-users";










data () {
  return {
    NewUsers
  }
}
```


# 使用：
```html
<component :is="NewUsers" ref="NewUsers"  />
```

# 案例：
![](https://quanyi.blog.csdn.net/article/details/113755417) 
