---
title: 用js打开电脑的软件

index_img: https://img-blog.csdnimg.cn/20191029160046941.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---











 ActiveXObject("WScript.Shell")
 ==只支持IE浏览器==
比如打开Typroa软件：
![用js打开电脑的软件](https://img-blog.csdnimg.cn/20191029155704185.png)


```javascript
// 创建ActiveXObject实例，只在IE下有效，才可以创建
  var objShell= new ActiveXObject("WScript.Shell");
  // 用谷歌浏览器打开链接
  objShell.Run("cmd.exe /c start Typroa",0,true);
  /* 命令参数说明
  cmd.exe /c dir 是执行完dir命令后关闭命令窗口。
  cmd.exe /k dir 是执行完dir命令后不关闭命令窗口。
  cmd.exe /c start dir 会打开一个新窗口后执行dir指令，原窗口会关闭。
  cmd.exe /k start dir 会打开一个新窗口后执行dir指令，原窗口不会关闭。
   */
```
没错，就这么两行代码


---

效果：

![用js打开电脑的软件](https://img-blog.csdnimg.cn/20191029160046941.gif)



