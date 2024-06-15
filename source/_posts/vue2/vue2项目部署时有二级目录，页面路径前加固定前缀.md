---
title: vue2项目部署时有二级目录，页面路径前加固定前缀

index_img: https://img-blog.csdnimg.cn/2020093010040933.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





比如：
![vue项目 路径前加固定前缀](https://img-blog.csdnimg.cn/2020093010040933.png#pic_center)

# vue init项目：
`config/index.js`文件，build对象下的`assetsPublicPath`属性，值为`你的前缀`即可：
![vue项目 路径前加固定前缀](https://img-blog.csdnimg.cn/20200930100504738.png#pic_center)

`src/router/index.js`文件，加入`base`属性，**值和上面的一样**
![vue项目 路径前加固定前缀](https://img-blog.csdnimg.cn/20200930100648858.png#pic_center)


搞定！
![vue项目 路径前加固定前缀](https://img-blog.csdnimg.cn/20200930100954146.gif#pic_center)

---

vue router配置：[https://blog.csdn.net/weixin_34026484/article/details/91462668?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param](https://blog.csdn.net/weixin_34026484/article/details/91462668?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param)


**部署后图片加载不出来的话：** 修改引用static文件夹中的图片地址
- **html**部分的==img==标签地址， 将/static改为`@/../static`，如图：
 ![](https://img-blog.csdnimg.cn/20201022162135252.png)
  如果是通过js动态引入的src，就使换成二级目录：`/fs/static/img/bg.png`


- **css**部分的==backgroud==属性引入的图片，将/static改为`../../static`，如图：
![](https://img-blog.csdnimg.cn/20201022162139227.png)
如果部署线上找不到图片，就不用../../，也用二级目录：`/fs/static/img/bg.png`，虽然在本地开发中显示不出来，但部署线上可以。



---

# vue create项目：
![](https://img-blog.csdnimg.cn/d86a67af38244b27a71e2a558b782ea1.png)

![](https://img-blog.csdnimg.cn/996b8a27f48d4a35a65a77b77cd9083a.png)
