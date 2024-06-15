---
title: vite+vue3项目采用ejs语法配置cdn引入在线依赖

index_img: https://img-blog.csdnimg.cn/16e9b5badc0641f49e027b97c29c989b.png
lazyload: true
categories:
- vue3
tags:
- vue3



---












采用[ejs](https://www.npmjs.com/package/vite-plugin-ejs)的方式
# 安装语法依赖
```
npm install vite-plugin-ejs -D
```

# 配置暴露数据
vite.config.js文件：

```javascript
import { fileURLToPath, URL } from 'node:url'
import { defineConfig, loadEnv } from 'vite'
import vue from '@vitejs/plugin-vue'
import vueJsx from '@vitejs/plugin-vue-jsx'
import { ViteEjsPlugin } from 'vite-plugin-ejs'







const ejsData = {
  // ejs读取环境变量
  ENV: loadEnv(process.env.VITE_USER_NODE_ENV, process.cwd(), ''),
  // CDN外链，ejs会插入到index.html中
  CDNs: {
    css: [
      "https://unpkg.com/animate.css@4.1.1",
      "https://unpkg.com/bootstrap@5.3.1/dist/css/bootstrap.min.css",
      "https://unpkg.com/bootstrap-icons@1.10.0/font/bootstrap-icons.css"
    ],
    js: [
      "https://unpkg.com/@popperjs/core@2.11.6/dist/umd/popper.min.js",
      "https://unpkg.com/bootstrap@5.3.1/dist/js/bootstrap.min.js"
    ]
  }
}

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [
    vue(),
    vueJsx(),
    ViteEjsPlugin(ejsData)
  ],
  resolve: {
    alias: {
      '@': fileURLToPath(new URL('./src', import.meta.url))
    }
  }
})

```

看到`ViteEjsPlugin(ejsData)`了吗，就是这个方法，把你定义的ejsData变量暴露到了index.html文件

# 使用数据

```html
<!DOCTYPE html>
<html lang="zh-cn">
  <head>
    <meta charset="UTF-8">
    <link rel="icon" href="/logo.png">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title><%= ENV.VITE_APP_TITLE %></title>
      <% for (let path of CDNs.css) { %>
        <link href="<%= path %>" rel="preload" as="style" />
        <link href="<%= path %>" rel="stylesheet" />
      <% } %>
  </head>
  <body>
    <div id="app"></div>

    <script type="module" src="/src/main.js"></script>
    <% for (let path of CDNs.js) { %>
      <script defer src="<%= path %>"></script>
    <% } %>
  </body>
</html>

```
看到了吗？`ENV.VITE_APP_TITLE`和`CDNs.css    、    CDNs.js`都是[ejs](https://www.npmjs.com/package/vite-plugin-ejs)暴露出来的，采用[ejs](https://ejs.bootcss.com/)循环CDNs的数据即可

# 效果
![](https://img-blog.csdnimg.cn/16e9b5badc0641f49e027b97c29c989b.png)


