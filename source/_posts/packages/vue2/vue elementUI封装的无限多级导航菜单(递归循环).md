---
title: vue elementUI封装的无限多级导航菜单(递归循环)

index_img: https://img-blog.csdnimg.cn/22043757f1f14754ae796c78930753a1.png
lazyload: true
categories:
- vue2
- 拿来主义
tags:
- vue2
- elementUI
- 无限多级导航菜单

---













![](https://img-blog.csdnimg.cn/e3421347d01d4a8ba0659a9be63dc4f4.png)





需要封装成两个文件：
![](https://img-blog.csdnimg.cn/64a44f6bc75e44e6a5cd6a8c4ce8b5a7.png)

1. `menu/index.vue`

```html
<template>
  <el-menu
    class="box-card"
    unique-opened
    :collapse="$store.state.isCollapse"
    :default-active="$store.state.nowPage"
    background-color="#2f3332"
    text-color="#fff"
    active-text-color="#4af4d2"
  >
    <MenuList :data="$store.state.permissionMenu"></MenuList>
  </el-menu>
</template>

<script>
/**
 * @author        全易
 * @time          2020-10-05 16:38:30  星期一
 * @description   菜单栏
 */
import MenuList from "./list";

export default {
  name: "Menu",
  components: {
    MenuList,
  },
};
</script>

<style lang="less" scoped>
.no-menus {
  color: #ffffff;
  padding: 15px;
}
.fa {
  vertical-align: middle;
  margin-right: 5px;
  width: 24px;
  text-align: center;
}
.box-card {
  border: none;
  height: 100vh;
  overflow: auto;
  .menu {
    height: calc(100vh - 175px);
    overflow: auto;
  }
  .often {
    z-index: 1;
    position: sticky;
    top: 0;
    color: #ffffff;
    padding: 10px 0;
    border-bottom: 1px solid #6b6b6b;
    background-color: #2f3332;
    .title {
      margin-bottom: 8px;
      padding-left: 8px;
    }
    .item {
      height: 28px;
      line-height: 28px;
      font-size: 12px;
    }
  }
}
</style>

```






2. `menu/list.vue`
注意这个文件用到了`vue-fragment`插件，需要安装
```html
<template>
  <vue-fragment class="menu-list">
    <template v-for="item in data">
      <el-menu-item
        v-if="item.children.length < 1"
        :key="item.menuIdStr"
        :index="item.menuIdStr"
        @click="goPage(item)"
      >
        <i :class="item.icon"></i>
        <span slot="title">{{ item.menuName }}</span>
      </el-menu-item>
      <el-submenu v-else :key="item.menuIdStr" :index="item.menuIdStr">
        <template slot="title">
          <i :class="item.icon"></i>
          <span slot="title">{{ item.menuName }}</span>
        </template>
        <MenuList :data="item.children"></MenuList>
      </el-submenu>
    </template>
  </vue-fragment>
</template>

<script>
/**
 * @author        全易
 * @time          2021-04-26 08:48:57  星期一
 * @description   菜单栏列表
 */
import { Fragment } from 'vue-fragment'

export default {
  name: "MenuList",
  components: { 'vue-fragment':Fragment },
  props: {
    data: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  methods: {
    // 跳转页面
    goPage(page) {
      // console.log(page);
      if (this.$route.path !== page.url) {
        this.$router.push(page.url);
      }
    },
  },
};
</script>

<style lang="less" scoped>
.fa {
  vertical-align: middle;
  margin-right: 5px;
  width: 24px;
  text-align: center;
}
</style>

```


两个文件封装完成，在使用的地方引入就好了
![](https://img-blog.csdnimg.cn/81fa68005bc04f4db67780c7ed70d670.png)



---


> 也可以直接安装个[组件](https://www.npmjs.com/package/element-navmenu_vue) `npm install element-navmenu_vue`


![](https://img-blog.csdnimg.cn/22043757f1f14754ae796c78930753a1.png)




