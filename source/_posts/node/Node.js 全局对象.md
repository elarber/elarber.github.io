---
title: Node.js 全局对象

index_img: https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240411233910560.png
lazyload: true
categories:
- node
tags:
- node



---













> 和js一样，基本所有语法都是可以使用的。node本身就是js嘛，小区别就在于有个别部分的对象是面向浏览器的api，在node环境就**不能用**了，因为node是服务器端，在服务环境下新增了其他api搭配各类插件即可开发





# __filename

表示当前正在执行的脚本的文件名。它将输出文件所在位置的绝对路径，且和命令行参数所指定的文件名不一定相同。 如果在模块中，返回的值是模块文件的路径。

![](https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240411231655145.png)







# __dirname

**__dirname** 表示当前执行脚本所在的目录。

![](https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240411231849313.png)





# process

用于描述当前Node.js 进程状态的对象，提供了一个与操作系统的简单接口。通常在你写本地命令行程序的时候，少不了要 和它打交道。

![](https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240411232553130.png)



![](https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240411233132589.png)



![](https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240411233910560.png)

