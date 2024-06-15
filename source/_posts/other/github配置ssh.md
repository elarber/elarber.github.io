---
title: github配置ssh

index_img: 
lazyload: true
categories:
- 前端周边
tags:
- git
- github



---












# 生成公钥
在电脑用户的目录下打开终端执行 `ssh-keygen -t rsa`:
![](https://img-blog.csdnimg.cn/direct/1dea164e4a4340b18ad33290f7bb4ac5.png)
执行完不要关

# 配置文件
看看用户的目录里 .ssh 目录：
![](https://img-blog.csdnimg.cn/direct/39287052606a44f9909319f51b9c06dd.png)

```
Host github.com
  Hostname ssh.github.com
  Port 443
```



# 配置公钥
复制 id_rsa.pub 文件里的内容
![](https://img-blog.csdnimg.cn/direct/a94dd3694c924c8b973af9885cec6553.png)

粘贴到 github上
![](https://img-blog.csdnimg.cn/direct/e5df068f1ca94534b49da077b80553e2.png)
![](https://img-blog.csdnimg.cn/direct/45c2edf01fd64060baf3a9dccbc49f3e.png)


# 连接密钥
回到刚才的终端执行 `ssh -T git@github.com`
![](https://img-blog.csdnimg.cn/direct/0e852f02802141f7bc5714d4e0d505bd.png)

成功了

