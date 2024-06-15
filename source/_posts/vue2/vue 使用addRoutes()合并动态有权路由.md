---
title: vue 使用addRoutes()合并动态有权路由

index_img: https://img-blog.csdnimg.cn/20210315162234797.gif
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





### 给出默认的静态路由
![](https://img-blog.csdnimg.cn/20210315163153329.png)


### 登陆成功后调用获取有权路由接口：
---
![](https://img-blog.csdnimg.cn/20210315162234797.gif#pic_center)

![](https://img-blog.csdnimg.cn/20210315162225604.png)



### 在调用`refresh`接口时处理返回数据
---

![](https://img-blog.csdnimg.cn/20210315165204973.png)





1. 合并有权路由
调用vueX的`setRouters`函数合并有权路由：
![](https://img-blog.csdnimg.cn/20210315162843228.png)

```javascript
  // 设置权限路由
  setRouters(state, data) {
    // console.log("接口返回路由信息：", data);
    // 5/1. 扁平化路由数据封装
    let flatRoute = [];
    function flattening(menu) {
      menu.map((item) => {
        // console.log(item);
        if (item.children) {
          flattening(item.children); // 递归执行
        }
        flatRoute.push(item);
      });
    }
    flattening(data); // 调用执行扁平化路由数据
    // console.log("扁平化路由：",flatRoute);

    // 5/2. 去除目录
    let noDirectoryRoute = flatRoute.filter((item) => {
      // console.log(item);
      if (item.url !== "") {
        return item
      }
    });
    // console.log("路由数据：", noDirectoryRoute);

    // 5/3. 结构化有权路由
    let structuringRoute = noDirectoryRoute.map(item => {
      const component = require(`@/pages${item.url}/index`);
      return {
        path: item.url,
        name: component.default.name,
        component: component.default,
        meta: {
          title: item.menuName,
          id: item.menuIdStr
        }
      }
    });
    // console.log("结构化的路由：", structuringRoute);

    // 5/4. 合并有权路由
    router.addRoutes([
      {
        path: '/',
        name: 'Main',
        component: () => import("@/pages/main.vue"),
        redirect: "/home",
        children: structuringRoute
      }
    ]);

    // 5/5. 存储有权路由集合
    state.permissionRouters = ["/login", "/404", "/"];
    state.permissionRouters.push(...noDirectoryRoute.map(item => {
      return item.url;
    }))
  },
```




2. 渲染菜单栏
![](https://img-blog.csdnimg.cn/20210315162933587.png)


```javascript
  // 设置权限菜单
  setMenu(state, data) {
    state.permissionMenu = data;
  },
```


### 导航守卫拦截无权跳转
---

![](https://img-blog.csdnimg.cn/20210315163900682.png)

```javascript
// 全局前置守卫
router.beforeEach((to, from, next) => {
  // console.log(to, from);

  // 2/1. 判断访问越权
  // console.log(store.state.permissionRouters);
  let paths = store.state.permissionRouters;
  if (!paths.includes(to.path)) {
    next({ path: '/404' })
  }

  // 2/2. 判断登陆情况
  const token = sessionStorage.getItem("X-Token");
  if (!token) {
    if (to.path !== "/login") {
      // alert("未登录，请先登录！")
      store.commit("clearnUserRelated");
      next({ path: '/login' })
    }
  }

  // 满足以上条件，才能过 
  next();
  // 插入到经常访问的路由记录里
  store.commit("setOftenURL", {
    title: to.meta.title,
    url: to.path
  });

})
```


### 防止刷新路由不在了
---
在入口文件`App.vue`再调一遍`refresh`接口
![](https://img-blog.csdnimg.cn/202103151643537.png)




`refresh`接口返回的路由数据结构：

```json
{
    "code":0,
    "data":{
        "menuList":[
            {
                "searchValue":"",
                "createId":"",
                "createBy":"admin",
                "createTime":"2021-01-11 15:09:58",
                "updateId":"",
                "updateBy":"",
                "updateTime":"",
                "deleted":"",
                "remark":"",
                "params":"",
                "menuId":1369,
                "menuName":"首页",
                "parentName":"",
                "parentId":0,
                "orderNum":"0",
                "url":"/home",
                "menuType":"C",
                "visible":"0",
                "perms":"0",
                "icon":"fa fa-newspaper-o",
                "menuIdStr":"1369",
                "children":[

                ]
            },
            {
                "searchValue":"",
                "createId":"",
                "createBy":"admin",
                "createTime":"2020-12-25 12:06:48",
                "updateId":"",
                "updateBy":"",
                "updateTime":"",
                "deleted":"",
                "remark":"",
                "params":"",
                "menuId":1364,
                "menuName":"管理中心",
                "parentName":"",
                "parentId":0,
                "orderNum":"1",
                "url":"",
                "menuType":"M",
                "visible":"0",
                "perms":"1",
                "icon":"el-icon-set-up",
                "menuIdStr":"1364",
                "children":[
                    {
                        "searchValue":"",
                        "createId":"",
                        "createBy":"admin",
                        "createTime":"2020-12-25 12:11:19",
                        "updateId":"",
                        "updateBy":"",
                        "updateTime":"",
                        "deleted":"",
                        "remark":"",
                        "params":"",
                        "menuId":1367,
                        "menuName":"用电用户管理",
                        "parentName":"",
                        "parentId":1364,
                        "orderNum":"11",
                        "url":"/management/use-electric",
                        "menuType":"C",
                        "visible":"0",
                        "perms":"11",
                        "icon":"fa fa-user",
                        "menuIdStr":"1367",
                        "children":[

                        ]
                    },
                    {
                        "searchValue":"",
                        "createId":"",
                        "createBy":"admin",
                        "createTime":"2020-12-25 12:11:43",
                        "updateId":"",
                        "updateBy":"",
                        "updateTime":"",
                        "deleted":"",
                        "remark":"",
                        "params":"",
                        "menuId":1368,
                        "menuName":"运营用户管理",
                        "parentName":"",
                        "parentId":1364,
                        "orderNum":"12",
                        "url":"/management/operation",
                        "menuType":"C",
                        "visible":"0",
                        "perms":"12",
                        "icon":"fa fa-pie-chart",
                        "menuIdStr":"1368",
                        "children":[

                        ]
                    },
                    {
                        "searchValue":"",
                        "createId":"",
                        "createBy":"admin",
                        "createTime":"2020-12-25 12:42:38",
                        "updateId":"",
                        "updateBy":"",
                        "updateTime":"",
                        "deleted":"",
                        "remark":"",
                        "params":"",
                        "menuId":1370,
                        "menuName":"角色管理",
                        "parentName":"",
                        "parentId":1364,
                        "orderNum":"13",
                        "url":"/management/role",
                        "menuType":"C",
                        "visible":"0",
                        "perms":"13",
                        "icon":"fa fa-user-secret",
                        "menuIdStr":"1370",
                        "children":[

                        ]
                    },
                    {
                        "searchValue":"",
                        "createId":"",
                        "createBy":"admin",
                        "createTime":"2021-03-15 15:22:02",
                        "updateId":"",
                        "updateBy":"",
                        "updateTime":"",
                        "deleted":"",
                        "remark":"",
                        "params":"",
                        "menuId":1371,
                        "menuName":"资源管理",
                        "parentName":"",
                        "parentId":1364,
                        "orderNum":"14",
                        "url":"/management/resource",
                        "menuType":"C",
                        "visible":"0",
                        "perms":"14",
                        "icon":"fa fa-chain",
                        "menuIdStr":"1371",
                        "children":[

                        ]
                    },
                    {
                        "searchValue":"",
                        "createId":"",
                        "createBy":"admin",
                        "createTime":"2020-12-25 12:44:22",
                        "updateId":"",
                        "updateBy":"",
                        "updateTime":"",
                        "deleted":"",
                        "remark":"",
                        "params":"",
                        "menuId":1372,
                        "menuName":"组织管理",
                        "parentName":"",
                        "parentId":1364,
                        "orderNum":"15",
                        "url":"/management/organization",
                        "menuType":"C",
                        "visible":"0",
                        "perms":"15",
                        "icon":"fa fa-sitemap",
                        "menuIdStr":"1372",
                        "children":[

                        ]
                    }
                ]
            },
            {
                "searchValue":"",
                "createId":"",
                "createBy":"admin",
                "createTime":"2021-01-18 10:40:12",
                "updateId":"",
                "updateBy":"",
                "updateTime":"",
                "deleted":"",
                "remark":"",
                "params":"",
                "menuId":1373,
                "menuName":"资产中心",
                "parentName":"",
                "parentId":0,
                "orderNum":"2",
                "url":"",
                "menuType":"M",
                "visible":"0",
                "perms":"2",
                "icon":"fa fa-cubes",
                "menuIdStr":"1373",
                "children":[
                    {
                        "searchValue":"",
                        "createId":"",
                        "createBy":"admin",
                        "createTime":"2020-12-25 12:45:47",
                        "updateId":"",
                        "updateBy":"",
                        "updateTime":"",
                        "deleted":"",
                        "remark":"",
                        "params":"",
                        "menuId":1374,
                        "menuName":"电站管理",
                        "parentName":"",
                        "parentId":1373,
                        "orderNum":"21",
                        "url":"/balance/power-stations",
                        "menuType":"C",
                        "visible":"0",
                        "perms":"21",
                        "icon":"fa fa-podcast",
                        "menuIdStr":"1374",
                        "children":[

                        ]
                    },
                    {
                        "searchValue":"",
                        "createId":"",
                        "createBy":"admin",
                        "createTime":"2020-12-25 12:46:18",
                        "updateId":"",
                        "updateBy":"",
                        "updateTime":"",
                        "deleted":"",
                        "remark":"",
                        "params":"",
                        "menuId":1375,
                        "menuName":"设备管理",
                        "parentName":"",
                        "parentId":1373,
                        "orderNum":"22",
                        "url":"/balance/equipment",
                        "menuType":"C",
                        "visible":"0",
                        "perms":"22",
                        "icon":"fa fa-circle-o-notch",
                        "menuIdStr":"1375",
                        "children":[

                        ]
                    },
                    {
                        "searchValue":"",
                        "createId":"",
                        "createBy":"admin",
                        "createTime":"2021-01-20 16:07:35",
                        "updateId":"",
                        "updateBy":"",
                        "updateTime":"",
                        "deleted":"",
                        "remark":"",
                        "params":"",
                        "menuId":1409,
                        "menuName":"电表管理",
                        "parentName":"",
                        "parentId":1373,
                        "orderNum":"23",
                        "url":"/balance/ammeter",
                        "menuType":"C",
                        "visible":"0",
                        "perms":"23",
                        "icon":"fa fa-clock-o",
                        "menuIdStr":"1409",
                        "children":[

                        ]
                    }
                ]
            },
            {
                "searchValue":"",
                "createId":"",
                "createBy":"admin",
                "createTime":"2020-12-25 12:58:10",
                "updateId":"",
                "updateBy":"",
                "updateTime":"",
                "deleted":"",
                "remark":"",
                "params":"",
                "menuId":1376,
                "menuName":"订单中心",
                "parentName":"",
                "parentId":0,
                "orderNum":"3",
                "url":"",
                "menuType":"M",
                "visible":"0",
                "perms":"3",
                "icon":"el-icon-document",
                "menuIdStr":"1376",
                "children":[
                    {
                        "searchValue":"",
                        "createId":"",
                        "createBy":"admin",
                        "createTime":"2020-12-25 12:59:00",
                        "updateId":"",
                        "updateBy":"",
                        "updateTime":"",
                        "deleted":"",
                        "remark":"",
                        "params":"",
                        "menuId":1377,
                        "menuName":"订单管理",
                        "parentName":"",
                        "parentId":1376,
                        "orderNum":"31",
                        "url":"/orders/order-manage",
                        "menuType":"C",
                        "visible":"0",
                        "perms":"31",
                        "icon":"el-icon-notebook-1",
                        "menuIdStr":"1377",
                        "children":[

                        ]
                    }
                ]
            },
            {
                "searchValue":"",
                "createId":"",
                "createBy":"admin",
                "createTime":"2020-12-25 13:00:23",
                "updateId":"",
                "updateBy":"",
                "updateTime":"",
                "deleted":"",
                "remark":"",
                "params":"",
                "menuId":1379,
                "menuName":"清算中心",
                "parentName":"",
                "parentId":0,
                "orderNum":"4",
                "url":"",
                "menuType":"M",
                "visible":"0",
                "perms":"4",
                "icon":"el-icon-finished",
                "menuIdStr":"1379",
                "children":[
                    {
                        "searchValue":"",
                        "createId":"",
                        "createBy":"admin",
                        "createTime":"2020-12-25 13:01:06",
                        "updateId":"",
                        "updateBy":"",
                        "updateTime":"",
                        "deleted":"",
                        "remark":"",
                        "params":"",
                        "menuId":1380,
                        "menuName":"计费模型",
                        "parentName":"",
                        "parentId":1379,
                        "orderNum":"41",
                        "url":"/settlement/billing-templates",
                        "menuType":"C",
                        "visible":"0",
                        "perms":"41",
                        "icon":"el-icon-c-scale-to-original",
                        "menuIdStr":"1380",
                        "children":[

                        ]
                    },
                    {
                        "searchValue":"",
                        "createId":"",
                        "createBy":"admin",
                        "createTime":"2021-03-08 13:24:14",
                        "updateId":"",
                        "updateBy":"",
                        "updateTime":"",
                        "deleted":"",
                        "remark":"",
                        "params":"",
                        "menuId":1385,
                        "menuName":"用户账户",
                        "parentName":"",
                        "parentId":1379,
                        "orderNum":"47",
                        "url":"/settlement/user-account",
                        "menuType":"C",
                        "visible":"0",
                        "perms":"47",
                        "icon":"el-icon-news",
                        "menuIdStr":"1385",
                        "children":[

                        ]
                    },
                    {
                        "searchValue":"",
                        "createId":"",
                        "createBy":"admin",
                        "createTime":"2021-02-03 13:42:18",
                        "updateId":"",
                        "updateBy":"",
                        "updateTime":"",
                        "deleted":"",
                        "remark":"",
                        "params":"",
                        "menuId":1411,
                        "menuName":"财务对账",
                        "parentName":"",
                        "parentId":1379,
                        "orderNum":"49",
                        "url":"/settlement/reconciliation",
                        "menuType":"C",
                        "visible":"0",
                        "perms":"settlement-reconciliation",
                        "icon":"fa fa-check-square-o",
                        "menuIdStr":"1411",
                        "children":[

                        ]
                    }
                ]
            },
            {
                "searchValue":"",
                "createId":"",
                "createBy":"admin",
                "createTime":"2021-01-12 12:04:03",
                "updateId":"",
                "updateBy":"",
                "updateTime":"",
                "deleted":"",
                "remark":"",
                "params":"",
                "menuId":1389,
                "menuName":"运监中心",
                "parentName":"",
                "parentId":0,
                "orderNum":"5",
                "url":"",
                "menuType":"M",
                "visible":"0",
                "perms":"5",
                "icon":"fa fa-bar-chart",
                "menuIdStr":"1389",
                "children":[
                    {
                        "searchValue":"",
                        "createId":"",
                        "createBy":"admin",
                        "createTime":"2020-12-25 13:11:56",
                        "updateId":"",
                        "updateBy":"",
                        "updateTime":"",
                        "deleted":"",
                        "remark":"",
                        "params":"",
                        "menuId":1390,
                        "menuName":"工单管理",
                        "parentName":"",
                        "parentId":1389,
                        "orderNum":"51",
                        "url":"/operational/work-order",
                        "menuType":"C",
                        "visible":"0",
                        "perms":"51",
                        "icon":"el-icon-chat-line-square",
                        "menuIdStr":"1390",
                        "children":[

                        ]
                    },
                    {
                        "searchValue":"",
                        "createId":"",
                        "createBy":"admin",
                        "createTime":"2021-01-06 16:34:36",
                        "updateId":"",
                        "updateBy":"",
                        "updateTime":"",
                        "deleted":"",
                        "remark":"",
                        "params":"",
                        "menuId":1392,
                        "menuName":"帮助管理",
                        "parentName":"",
                        "parentId":1389,
                        "orderNum":"53",
                        "url":"/operational/helps",
                        "menuType":"C",
                        "visible":"0",
                        "perms":"53",
                        "icon":"el-icon-service",
                        "menuIdStr":"1392",
                        "children":[

                        ]
                    },
                    {
                        "searchValue":"",
                        "createId":"",
                        "createBy":"admin",
                        "createTime":"2021-01-06 16:34:42",
                        "updateId":"",
                        "updateBy":"",
                        "updateTime":"",
                        "deleted":"",
                        "remark":"",
                        "params":"",
                        "menuId":1393,
                        "menuName":"用户反馈",
                        "parentName":"",
                        "parentId":1389,
                        "orderNum":"54",
                        "url":"/operational/users-feedbck",
                        "menuType":"C",
                        "visible":"0",
                        "perms":"54",
                        "icon":"el-icon-document-checked",
                        "menuIdStr":"1393",
                        "children":[

                        ]
                    },
                    {
                        "searchValue":"",
                        "createId":"",
                        "createBy":"admin",
                        "createTime":"2021-01-11 16:18:16",
                        "updateId":"",
                        "updateBy":"",
                        "updateTime":"",
                        "deleted":"",
                        "remark":"",
                        "params":"",
                        "menuId":1406,
                        "menuName":"运行管理",
                        "parentName":"",
                        "parentId":1389,
                        "orderNum":"56",
                        "url":"/operational/runing",
                        "menuType":"C",
                        "visible":"0",
                        "perms":"56",
                        "icon":"fa fa-superpowers",
                        "menuIdStr":"1406",
                        "children":[

                        ]
                    },
                    {
                        "searchValue":"",
                        "createId":"",
                        "createBy":"admin",
                        "createTime":"2021-01-19 16:18:55",
                        "updateId":"",
                        "updateBy":"",
                        "updateTime":"",
                        "deleted":"",
                        "remark":"",
                        "params":"",
                        "menuId":1408,
                        "menuName":"活动管理",
                        "parentName":"",
                        "parentId":1389,
                        "orderNum":"57",
                        "url":"/operational/events",
                        "menuType":"C",
                        "visible":"0",
                        "perms":"57",
                        "icon":"fa fa-signing",
                        "menuIdStr":"1408",
                        "children":[

                        ]
                    }
                ]
            },
            {
                "searchValue":"",
                "createId":"",
                "createBy":"admin",
                "createTime":"2021-01-08 13:45:12",
                "updateId":"",
                "updateBy":"",
                "updateTime":"",
                "deleted":"",
                "remark":"",
                "params":"",
                "menuId":1399,
                "menuName":"决策中心",
                "parentName":"",
                "parentId":0,
                "orderNum":"6",
                "url":"",
                "menuType":"M",
                "visible":"0",
                "perms":"6",
                "icon":"fa fa-legal",
                "menuIdStr":"1399",
                "children":[
                    {
                        "searchValue":"",
                        "createId":"",
                        "createBy":"admin",
                        "createTime":"2021-01-07 18:01:18",
                        "updateId":"",
                        "updateBy":"",
                        "updateTime":"",
                        "deleted":"",
                        "remark":"",
                        "params":"",
                        "menuId":1400,
                        "menuName":"平台驾驶舱",
                        "parentName":"",
                        "parentId":1399,
                        "orderNum":"61",
                        "url":"/overviews/platform",
                        "menuType":"C",
                        "visible":"0",
                        "perms":"61",
                        "icon":"fa fa-line-chart",
                        "menuIdStr":"1400",
                        "children":[

                        ]
                    }
                ]
            },
            {
                "searchValue":"",
                "createId":"",
                "createBy":"admin",
                "createTime":"2021-03-09 13:22:05",
                "updateId":"",
                "updateBy":"",
                "updateTime":"",
                "deleted":"",
                "remark":"",
                "params":"",
                "menuId":1395,
                "menuName":"个人中心",
                "parentName":"",
                "parentId":0,
                "orderNum":"99999",
                "url":"/my/center",
                "menuType":"F",
                "visible":"0",
                "perms":"01",
                "icon":"",
                "menuIdStr":"1395",
                "children":[

                ]
            },
            {
                "searchValue":"",
                "createId":"",
                "createBy":"admin",
                "createTime":"2021-03-09 13:19:15",
                "updateId":"",
                "updateBy":"",
                "updateTime":"",
                "deleted":"",
                "remark":"",
                "params":"",
                "menuId":1396,
                "menuName":"我的资料",
                "parentName":"",
                "parentId":0,
                "orderNum":"99999",
                "url":"/my/info",
                "menuType":"F",
                "visible":"0",
                "perms":"02",
                "icon":"",
                "menuIdStr":"1396",
                "children":[

                ]
            }
        ]
    },
    "msg":"操作成功",
    "errorMsg":"",
    "eternal":"",
    "eternal2":""
}
```
