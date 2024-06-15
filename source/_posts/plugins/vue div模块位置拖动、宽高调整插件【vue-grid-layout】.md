---
title: vue div模块位置拖动、宽高调整插件【vue-grid-layout】

index_img: https://img-blog.csdnimg.cn/20200805133913517.gif
lazyload: true
categories:
- 前端插件使用
tags:
- vue-grid-layout



---












![全易](https://img-blog.csdnimg.cn/20200805133913517.gif)


**github**：[https://github.com/jbaysolutions/vue-grid-layout](https://github.com/jbaysolutions/vue-grid-layout)

安装：
```
npm install vue-grid-layout --save
```


引入：
```
import VueGridLayout from 'vue-grid-layout';
```

使用：
```javascript
import VueGridLayout from "vue-grid-layout";

export default {
  data() {
    return {
    	draggable: false,
      	resizable:false,
		elements: [
		   { x: 0, y: 0, w: 2, h: 2, i: "0" },
		   { x: 2, y: 0, w: 2, h: 4, i: "1" },
		   { x: 4, y: 0, w: 2, h: 5, i: "2" },
		   { x: 6, y: 0, w: 2, h: 3, i: "3" },
		   { x: 8, y: 0, w: 2, h: 3, i: "4" },
		   { x: 10, y: 0, w: 2, h: 3, i: "5" },
		   { x: 0, y: 5, w: 2, h: 5, i: "6" },
		   { x: 2, y: 5, w: 2, h: 5, i: "7" },
		   { x: 4, y: 5, w: 2, h: 5, i: "8" },
		   { x: 6, y: 3, w: 2, h: 4, i: "9" },
		   { x: 8, y: 4, w: 2, h: 4, i: "10" },
		   { x: 10, y: 4, w: 2, h: 4, i: "11" },
		   { x: 0, y: 10, w: 2, h: 5, i: "12" },
		 ]
 	 }
  }，
  components: {
    GridLayout: VueGridLayout.GridLayout,
    GridItem: VueGridLayout.GridItem,
  },
  methods: {
	layoutCreatedEvent: function(newLayout){
      console.log("Created layout: ", newLayout)
    },
    layoutBeforeMountEvent: function(newLayout){
      console.log("beforeMount layout: ", newLayout)
    },
    layoutMountedEvent: function(newLayout){
      console.log("Mounted layout: ", newLayout)
    },
    layoutReadyEvent: function(newLayout){
      console.log("Ready layout: ", newLayout)
    },
    layoutUpdatedEvent: function(newLayout){
      console.log("Updated layout: ", newLayout)
    },
    moveEvent: function(i, newX, newY){
        console.log("MOVE i=" + i + ", X=" + newX + ", Y=" + newY);
    },
    resizeEvent: function(index, newH, newW, newHPx, newWPx){
      console.log("调整第" + index + "个, 宽=" + newH + "列, 高=" + newW + "行, 宽=" + newHPx + "px, 高=" + newWPx+"px");
    },
    movedEvent: function(i, newX, newY){
        console.log("MOVED i=" + i + ", X=" + newX + ", Y=" + newY);
    },
    resizedEvent: function(index, newH, newW, newHPx, newWPx){
      console.log("调整了第" + index + "个, 宽=" + newH + "列, 高=" + newW + "行, 宽=" + newHPx + "px, 高=" + newWPx+"px");
    },
  }
}
```

```html
<el-button type="primary" @click="draggable=!draggable; resizable=!resizable">改变布局</el-button>
<grid-layout
      :layout.sync="elements"
      :row-height="30"
      :is-draggable="draggable"
      :is-resizable="resizable"
	   @layout-created="layoutCreatedEvent"
       @layout-before-mount="layoutBeforeMountEvent"
       @layout-mounted="layoutMountedEvent"
       @layout-ready="layoutReadyEvent"
       @layout-updated="layoutUpdatedEvent"
>
      <grid-item
        v-for="item in elements"
        :x="item.x"
        :y="item.y"
        :w="item.w"
        :h="item.h"
        :i="item.i"
        :key="item.i"
		@resize="resizeEvent"
        @move="moveEvent"
        @resized="resizedEvent"
        @moved="movedEvent"
>
      {{item.i}}
     </grid-item>
</grid-layout>
```

```css
.vue-grid-item {
  border: 1px solid #dedede;
}
```


[https://github.com/dwanda/dragComponent](https://github.com/dwanda/dragComponent)
