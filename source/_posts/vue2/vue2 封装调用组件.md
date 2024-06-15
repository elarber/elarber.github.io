---
title: vue2 封装调用组件

index_img: https://img-blog.csdnimg.cn/20190705225621289.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





#### 一、创建组件
1. 添加个vue文件，就是你的**组件**。
![](https://img-blog.csdnimg.cn/20190705225621289.png)
2. 在这个组件里完善你要的组件样子、功能。
![](https://img-blog.csdnimg.cn/20190705225810382.png)

---

#### 二、调用组件
要哪个页面里显示这个组件就去哪个页面文件引入组件。
举个例子：我就在HelloWorld页面展示ADD组件的内容，所以我在`HelloWorld.vue`文件里调用了就。
==3== 个步骤：**导入组件**、**注册组件**、**调用组件**
![](https://img-blog.csdnimg.cn/20190705230239830.png)

---

效果出来了，如图：
![](https://img-blog.csdnimg.cn/20190705230423460.png)

---

全局批量封装组件及调用：[https://blog.csdn.net/qq_42618566/article/details/104396886](https://blog.csdn.net/qq_42618566/article/details/104396886)
