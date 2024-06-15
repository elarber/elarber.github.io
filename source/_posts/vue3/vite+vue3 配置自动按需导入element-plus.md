---
title: vite+vue3 配置自动按需导入element-plus

index_img: https://img-blog.csdnimg.cn/eff9f82f7dfc480b83be89a1068b1d1b.png
lazyload: true
categories:
- vue3
tags:
- vue3



---












# [安装element](https://element-plus.org/zh-CN/guide/installation.html#%E4%BD%BF%E7%94%A8%E5%8C%85%E7%AE%A1%E7%90%86%E5%99%A8)
```
npm install element-plus
```


# 自动导入
[安装自动导入的插件](https://element-plus.org/zh-CN/guide/quickstart.html#%E6%8C%89%E9%9C%80%E5%AF%BC%E5%85%A5):

```
npm install -D unplugin-vue-components unplugin-auto-import
```

# 配置
## vite
vite.config.js文件：

```javascript
import { defineConfig } from 'vite'
import AutoImport from 'unplugin-auto-import/vite'
import Components from 'unplugin-vue-components/vite'
import { ElementPlusResolver } from 'unplugin-vue-components/resolvers'

export default defineConfig({
  // ...
  plugins: [
    // ...
    AutoImport({
      resolvers: [ElementPlusResolver()],
    }),
    Components({
      resolvers: [ElementPlusResolver()],
    }),
  ],
})
```

## webpack

如果是webpack的话：vue.config.js

```javascript
const AutoImport = require('unplugin-auto-import/webpack')
const Components = require('unplugin-vue-components/webpack')
const { ElementPlusResolver } = require('unplugin-vue-components/resolvers')

module.exports = {
  // ...
  plugins: [
    AutoImport({
      resolvers: [ElementPlusResolver()],
    }),
    Components({
      resolvers: [ElementPlusResolver()],
    }),
  ],
}
```

大功告成！从始至终没有动过main.js文件哦。是不是很简单，官方也推荐自动导入的方式呢
![](https://img-blog.csdnimg.cn/eff9f82f7dfc480b83be89a1068b1d1b.png)

# 使用组件
比如[`el-image`](https://element-plus.org/en-US/component/image.html#basic-usage)
![](https://img-blog.csdnimg.cn/58bdc5b5d6e04a7baa42358e5af8ed3f.png)


![](https://img-blog.csdnimg.cn/9be61cb096094690b8bd4111ce3f3774.png)

