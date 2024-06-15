---
title: 前端使用vue-video-player做直播流视频

index_img: https://img-blog.csdnimg.cn/820ad10a296147c7b614c21fc71482c7.png
lazyload: true
categories:
- 前端插件使用
tags:
- vue-video-player
- 直播流视频



---













# 安装：

```javascript
npm install vue-video-player --save

npm install videojs-contrib-hls --save
```


# 引入：

```javascript
import VideoPlayer from 'vue-video-player'
require('video.js/dist/video-js.css')
require('vue-video-player/src/custom-theme.css')
import "videojs-contrib-hls"


Vue.use(VideoPlayer)
```


# 使用：

```html
<template>
  <div class="">
    <video-player
      ref="videoPlayer"
      class="video-player vjs-custom-skin"
      :playsinline="true"
      :options="playerOptions"
      @ready="playerReadied"
      @play="onPlayerPlay($event)"
      @pause="onPlayerPause($event)"
    />
  </div>
</template>

<script>
/**
 * @author        全易
 * @time          2022-01-19 14:06:46  星期三
 * @description   视频监控
 **/

export default {
  name: '',
  data() {
    return {
      playerOptions: {
        autoplay: true, // 如果true,浏览器准备好时开始回放。
        muted: false, // 默认情况下将会消除任何音频。
        loop: false, // 导致视频一结束就重新开始。
        preload: 'auto', // 建议浏览器在<video>加载元素后是否应该开始下载视频数据。auto浏览器选择最佳行为,立即开始加载视频（如果浏览器支持）
        language: 'zh-CN',
        aspectRatio: '16:9', // 将播放器置于流畅模式，并在计算播放器的动态大小时使用该值。值应该代表一个比例 - 用冒号分隔的两个数字（例如"16:9"或"4:3"）
        fluid: true, // 当true时，Video.js player将拥有流体大小。换句话说，它将按比例缩放以适应其容器。
        sources: [
          {
            type: 'application/x-mpegURL', // m3u8 类型
            src: 'https://logos-channel.scaleengine.net/logos-channel/live/biblescreen-ad-free/playlist.m3u8',
          },
        ],
        hls: true,
        width: '450',
        height: '200',
        notSupportedMessage: '无法播放',
        flash: { hls: { withCredentials: false } },
        html5: { hls: { withCredentials: false } },
        controlBar: {
          timeDivider: false, // 当前时间和持续时间的分隔符
          durationDisplay: true, // 显示持续时间
          remainingTimeDisplay: false, // 是否显示剩余时间功能
          fullscreenToggle: true, // 是否显示全屏按钮
        },
      },
    }
  },
  methods: {
    playerReadied(player) {
      var hls = player.tech({ IWillNotUseThisInPlugins: true }).hls
      player.tech_.hls.xhr.beforeRequest = function (options) {
        console.log(options)
        return options
      }
    },
    onPlayerPlay(e) {
      console.log(e)
    },
    onPlayerPause(e) {
      console.log(e)
    },
  },
}
</script>

<style lang="less" scoped>
</style>
```


# 效果：
![](https://img-blog.csdnimg.cn/820ad10a296147c7b614c21fc71482c7.png)
视频可能不稳定，接入特别慢，可能需要10来分钟


感谢：

> https://blog.csdn.net/niexier/article/details/117461895
> https://blog.csdn.net/wtyzky/article/details/103859955
