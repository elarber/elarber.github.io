---
title: vue2 使用directives指令注册全局权限指令

index_img: https://img-blog.csdnimg.cn/3abc008a78c543f9a9466161e3455596.png
lazyload: true
categories:
- vue2
- 拿来主义
tags:
- vue2
- 指令


---











```javascript
import $store from '@/store'
import { Notification } from 'element-ui'

// 全局指令
const directives = {
  // 权限
  permission(el, permission) {
    // console.log(permission);
    const allPermission = [...$store.state.permissionPublic, ...$store.state.permissionButtons];
    if (!allPermission.includes(permission.value)) {
      el.parentNode && el.parentNode.removeChild(el);
    }
  },

  // 复制文本
  // copy(el, data) {
  //   el.onclick = function () {
  //     if (!data.value && !el.innerText) return;
  //     let textarea = document.createElement("textarea");
  //     textarea.readOnly = 'readonly';
  //     textarea.value = data.value || el.innerText;
  //     el.appendChild(textarea);
  //     textarea.select();
  //     const result = document.execCommand("Copy");
  //     if (result) {
  //       Notification.success({
  //         duration: 1800,
  //         title: '复制成功',
  //         message: textarea.value,
  //         type: 'success'
  //       });
  //     } else {
  //       Notification.error({
  //         title: '错误',
  //         message: '复制失败'
  //       });
  //     }
  //     el.removeChild(textarea);
  //   }
  // }



}



export default {
  install(Vue) {
    Object.keys(directives).forEach(item => {
      Vue.directive(item, {
        inserted: directives[item]
      })
    })
  }
}
```

main.js入口文件：

```javascript


import directives from './directives/index.js'


Vue.use(directives);



```


那么在需要复制的地方就可以直接`v-permission`了
![](https://img-blog.csdnimg.cn/3abc008a78c543f9a9466161e3455596.png)
没有权限的摁钮就显示不出来了



