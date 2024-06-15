---
title: mac 安装 nvm 【真解决问题】

index_img: https://img-blog.csdnimg.cn/direct/69425a442f1f4e20adec80f1114ab866.png
lazyload: true
categories:
- 前端周边
tags:
- mac
- nvm



---











# 前提
- 没有node环境
- 已有git


# 下载
我用的gitee极速下载
```
git clone https://gitee.com/mirrors/nvm.git ~/.nvm && cd ~/.nvm && git checkout `git describe --abbrev=0 --tags`
```
![](https://img-blog.csdnimg.cn/direct/69425a442f1f4e20adec80f1114ab866.png)


# 配置
## 1. 配置变量
在用户的目录下新增文件== .zshrc ==
```
export NVM_DIR="$HOME/.nvm" 
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm 
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion" # This loads nvm bash_completion
```
![](https://img-blog.csdnimg.cn/direct/d6b71ca01df241828cec56508c513243.png)

## 2. 启用变量
```
source ~/.zshrc
```
![](https://img-blog.csdnimg.cn/direct/d8e800ed03ff49868f2380df11a4a24b.png)


`nvm -v`试试有版本号输出，成功了

