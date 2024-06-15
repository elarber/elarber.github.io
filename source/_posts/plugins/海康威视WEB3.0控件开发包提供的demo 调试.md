---
title: 海康威视WEB3.0控件开发包提供的demo 调试

index_img: https://img-blog.csdnimg.cn/450316e3ab9748f08f3e5ea6105151ff.png
lazyload: true
categories:
- 前端插件使用
tags:
- 海康威视
- 监控视频



---















# 设备概览：
1. 网线 ×3
2. 录像机 ×1
3. 交换机 ×1
4. 摄像头 ×1
![](https://img-blog.csdnimg.cn/315363706677401bb0eafcbb7cf9ee86.png)


# 设备间连接方式：
- 一根网线连接电脑到交换机
- 一根网线连接摄像头到交换机
- 一根网线连接录像机到交换机


==一定要保证设备之间在一个网段==


# 下载[官方demo](https://open.hikvision.com/download/5cda567cf47ae80dd41a54b3?type=10&id=4c945d18fa5f49638ce517ec32e24e24)
我这设备==不==支持websocket取流，所以需要[下载WEB3.0控件开发包 V3.0](https://blog.csdn.net/LAHM8963/article/details/121669529?spm=1001.2014.3001.5501)
![](https://img-blog.csdnimg.cn/380217ee376e40ee91d158d00d718907.png)

# 配置电脑环境
==因为要保证设备与电脑之间在一个网段嘛==
1. 先查看录像机的ip：
![](https://img-blog.csdnimg.cn/309f3fb996844e7e9e97bee291a9be0e.png)
2. 那么你的电脑也必须在192.168.1.啥啥啥：
![](https://img-blog.csdnimg.cn/f9c72fbad33b4cf78018b4fac9bfb538.png)
我就设置`192.168.1.111`了

验证下看看是不是：
![](https://img-blog.csdnimg.cn/e86e604373904d70a2125e8d44157653.png)
好的，是了




# 启动官方demo
1. 安装插件：
![](https://img-blog.csdnimg.cn/54c10f0c8f7b4b0798d166bf4f247385.png)

2. 启动环境：
![](https://img-blog.csdnimg.cn/df3e406e2bda490e8df4ad9ac653de08.png)

3. 在IE浏览器预览demo `http://127.0.0.1/`
![](https://img-blog.csdnimg.cn/450316e3ab9748f08f3e5ea6105151ff.png)

![](https://img-blog.csdnimg.cn/de67c20553964a6d94372a56c8dbc33d.png)

