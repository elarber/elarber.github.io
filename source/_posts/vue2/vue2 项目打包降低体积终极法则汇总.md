---
title: vue2 项目打包降低体积终极法则汇总

index_img: https://img-blog.csdnimg.cn/a580468b795f4ec59d86aa187bd81364.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





网上看了很多适用的不适用的办法，我这里分享给大家我一路实践过的优化之路吧
# 开启Gzip
这真的是个神插件
1. 安装插件：`npm i compression-webpack-plugin -D`
2. 在**vue.config.js**文件顶部引入：`const CompressionWebpackPlugin = require('compression-webpack-plugin');`
3. 在配置处使用

```javascript
module.exports = defineConfig({
  configureWebpack: {
    plugins: [
      new CompressionWebpackPlugin(), // 默认的配置就行
    ],
  }
})
```
打包看看，有`.gz`文件就对了：
![](https://img-blog.csdnimg.cn/a580468b795f4ec59d86aa187bd81364.png)




# 代码切片
使用webpack splitChunks配置将node_modules依赖进行切片，chunk-vendors.js文件就不至于很大。
在**vue.config.js**文件配置：
```javascript
module.exports = defineConfig({
  configureWebpack: {
    optimization: {
     runtimeChunk: true,
      splitChunks: {
        chunks: 'all',
        minSize: 1024,// 默认超过1k就抽离
        enforceSizeThreshold: 10240,
        cacheGroups: {
          //第三方库抽离
          vendor: {
            test: /node_modules/,
            name(module) {
              const pkg = module.context.match(/[\\/]node_modules[\\/](.*?)([\\/]|$)/);
              if (!pkg) {
                return;
              }
              return `npm.${pkg[1].replace('@', '')}`;
            },
          },
        }
      },
    }
  }
})
```


和上面比起来，**vendor-chunks.js**切片了，单个文件没那么大了
![](https://img-blog.csdnimg.cn/77de33858aa042a8afccd644da9b1318.png)


# cdn加载依赖
- [https://blog.csdn.net/qq_42618566](https://blog.csdn.net/qq_42618566)超简单，就两步
- 




# 自定义封装按需引入
自定义封装的组件、指令、过滤器，任何东西都千万不要在main.js引入，不要挂载全局！哪里需要哪里import
![](https://img-blog.csdnimg.cn/6c1881e56ddd4a3f8e3efe3612a722fb.png)

![](https://img-blog.csdnimg.cn/49d50f06cc3a4bda86f0fc3727b01469.png)
像这样：
![](https://img-blog.csdnimg.cn/c7e0b2fd88154a7681cfefc3b3891220.png)


尽可能的让**main.js**文件 import最少
![](https://img-blog.csdnimg.cn/626a9d92fff643d68fbb9af725a0ba46.png)



# 配置tree shaking 摇树优化
1. 在**vue.config.js**文件配置：
```javascript
configureWebpack: {
  optimization: {
    minimize: true,
     // sideEffects和usedExports是两种不同的优化方式。
     usedExports: true, // 识别无用代码 未使用的导出内容不会被生成 usedExports 依赖于 terser 去检测语句中的副作用。
     // sideEffects: true,  // 开启副作用标识功能 sideEffects更为有效是因为它允许跳过整个模块/文件和整个文件子树。
  }
}
```

2. package.json 配置：`"sideEffects": false,`
![](https://img-blog.csdnimg.cn/b6ed6aa1e5f0433f8fb64d198d14ebd0.png)
