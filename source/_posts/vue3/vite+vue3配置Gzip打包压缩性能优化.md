---
title: vite+vue3配置Gzip打包压缩性能优化

index_img: ttps://img-blog.csdnimg.cn/4b5cfa1ffe2d49f0816cc631d7794c87.png
lazyload: true
categories:
- vue3
tags:
- vue3



---











# [安装依赖](https://www.npmjs.com/package/vite-plugin-compress)
```
npm install vite-plugin-compression -D
```

# 使用依赖

```javascript
import viteCompression from 'vite-plugin-compression'
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'



// https://vitejs.dev/config/
export default defineConfig({
  plugins: [
    vue(),
    viteCompression({
      filter: /.(js|css|html|json|mjs|png|jpg|jpeg|svg)$/i  // 这些文件都要压缩
    }),
  ]
})
```

# 效果
npm run build之后你看你的dist目录，会有`.gz`文件：
![](https://img-blog.csdnimg.cn/17846120dc384590b28d36e9b2511e80.png)

![](https://img-blog.csdnimg.cn/4b5cfa1ffe2d49f0816cc631d7794c87.png)


到此前端需要配置的已经完成，需要服务器也配置Gzip





