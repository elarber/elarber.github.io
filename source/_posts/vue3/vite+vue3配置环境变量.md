---
title: vite+vue3配置环境变量

index_img: https://img-blog.csdnimg.cn/f242a6f11a4c4d5e85c250a1812c9f39.png
lazyload: true
categories:
- vue3
tags:
- vue3
- 环境配置


---











首先在项目根目录添加[环境文件](https://cn.vitejs.dev/guide/env-and-mode.html#env-files)，比如有测试环境

![](https://img-blog.csdnimg.cn/f242a6f11a4c4d5e85c250a1812c9f39.png)


# 环境说明
- `.env`：所有环境都会加载
- `.env.development`：开发环境加载
- `.env.production`：生产环境加载
- `.env.test`：测试环境加载


# 语法说明
> 变量名 = 值

例如通用环境：
![](https://img-blog.csdnimg.cn/194b2741d95f4cb883ac9b652baf4baa.png)



# 取环境变量

```javascript
console.log(import.meta.env);
```
输出看看有啥，取就完了。 如果想要在index.html读取，可以使用 [ejs](https://quanyi.blog.csdn.net/article/details/132333865) 语法，安装[vite-plugin-ejs](https://quanyi.blog.csdn.net/article/details/132333865)插件





