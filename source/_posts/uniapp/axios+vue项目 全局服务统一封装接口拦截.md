---
title: axios+vue项目 全局服务统一封装接口拦截

# index_img: /img/articles/
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





# 安装插件
```
npm install axios --save
```


# 服务封装
项目src/service/index.js文件：
```javascript
import axios from "axios"
import { Message } from "element-ui"
import $store from '@/store'
const httpCodes = require("@/config/http-code.json") // https://blog.csdn.net/qq_42618566/article/details/132541251


// axios.defaults.baseURL = process.env.NODE_ENV === "development" ? "/api" : process.env.VUE_APP_BASE_URL;
axios.defaults.headers = {
  'Content-Type': 'application/json; charset=utf-8'
}

// 请求拦截
axios.interceptors.request.use(
  (request) => {
    // console.log(request)
    // 你的逻辑
    const token = localStorage.getItem('token');
    request.headers['Authorization'] = "Bearer " + token;
   
    return request;
  },
  (error) => {
    return Promise.reject(error);
  }
);

// 响应拦截
axios.interceptors.response.use(
  (response) => {
    // console.log(response)
    // 你的逻辑
    if (response.data.code === 2001 && location.pathname !== "/logon") {
      $store.commit("logout", "1");
    }
    if (response.data.code !== 0) {
      Message.error(response.data.msg);
    }
    
    return response.data;
  },
  (error) => {
    // https://www.runoob.com/tags/html-httpmessages.html
    // https://www.runoob.com/http/http-status-codes.html
    const item = httpCodes.find(item => {
      return error.response.status === item.code;
    })
    Message.error(`${item.code}：${item.message}`);
    return Promise.reject(error)
  }
);




export default axios;
```


# 接口封装

```javascript
import http from './index' // 引入刚才封装的服务


  // 我的待办
 export function myTask (params, config) {
  return http.get("/service/demo/myTask.json", params, config)
 }

  // 任务委托
 export function taskEntrust: (params, config) {
  return http.post("/service/demo/setTaskAssignee", params, config)
 }

  // 我的已办
 export function myFinished: (params, config)  {
  return http.get("/service/demo/myFinished.json", params, config)
 }
```


可以使用了
