---
title: js 获取元素属性的值  ||  设置元素属性的值  ||  移除属性 || 增删改查类名

# index_img: 
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---











```javascript
// 1. 获取元素的属性值：  
element.getAttribute("属性");


// 2. 设置元素的属性值：  
element.setAttribute("属性","值");


// 3. 移除元素的属性：  
element.removeAttribute("属性");


			// 4 操作元素的类
// 4.1 添加一个或多个类名
element.classList.add('classone','classtwo',···);


// 4.2 删除一个或多个类名
element.classList.remove('classone','classtwo',···);


// 4.3 检索该类里是否有哪个类名
element.classList.indexOf('classname');
element.classList.contains('classname');
```


