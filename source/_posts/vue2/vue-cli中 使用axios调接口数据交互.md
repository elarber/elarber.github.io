---
title: vue-cli中 使用axios调接口数据交互

index_img: /img/articles/
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





**首先要安装了axios**
`npm install axios --save`

如下图：
![](https://img-blog.csdnimg.cn/20190705100636667.png)
**然后再main.js里配置下axios**

```
import Axios from 'axios'
Vue.prototype.$axios=Axios
```

如下图：
![](https://img-blog.csdnimg.cn/20190705100803683.png)
至此请求插件安装配置完毕
下面获取下数据看看
因为原生的样式太丑，我就用element了，那这样就需要安装和配置下element了，如下：
```
npm install element-ui --save
```
![](https://img-blog.csdnimg.cn/2019070510120842.png)
**仍然是在main.js里配置下element**

```
import ElementUI from 'element-ui'
import 'element-ui/lib/theme-chalk/index.css'



Vue.use(ElementUI);
```
如下图：
![](https://img-blog.csdnimg.cn/20190705101347157.png)
从[element的官网](https://element.eleme.cn/#/zh-CN/component/table)找个好看的表格复制过来
就它了
![](https://img-blog.csdnimg.cn/20190705101706947.png)
现在就进入正题了：获取动态数据！**调接口**，如下图：
![](https://img-blog.csdnimg.cn/20190705101954207.png)
带参数的话，可以拼接在url后面：

```javascript
	axios.get('/user',{ params:{ ID:12345，name:quanyi } }) .then(function(response){
	console.log(response); 
	}) .catch(function(err){
		console.log(err);
	});
```

注意下图中Prop的值是接口定义的属性名，不是我起的名字
![111111](https://img-blog.csdnimg.cn/20190705101840853.png)

**浏览器效果如下：**
![](https://img-blog.csdnimg.cn/20190705102520741.png)
**给代码：**

```
<template>
  <div class="HelloWorld">
    <h1>{{ msg }}</h1>
    <!-- <ul>
      <li v-for="(item,index) in items" :key="index">{{item.title}}</li>
    </ul> -->
    <el-row type="flex" justify="center">
      <el-col :span="16">
        <h3>element-ui的表格</h3>
        <el-table
          :data="tableData"
          style="width: 100%">
          <el-table-column
            type="index"
            label="序号"
            width="60">
          </el-table-column>
          <el-table-column
            prop="ptime"
            label="日期"
            width="180">
          </el-table-column>
          <el-table-column
            prop="docid"
            label="编号"
            width="180">
          </el-table-column>
          <el-table-column
            prop="title"
            label="内容">
          </el-table-column>
        </el-table>
      </el-col>
    </el-row>
    
    <table style="margin:80px auto;">
      <h3>原生表格</h3>
      <tr>
        <td>序号</td>
        <td>时间</td>
        <td>编号</td>
        <td>内容</td>
      </tr>
      <tr v-for="(datar,index) in datas" :key="index">
        <td>{{ index+1 }}</td>
        <td>{{ datar.ptime }}</td>
        <td>{{ datar.docid }}</td>
        <td>{{ datar.title }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      items:'',
      datas:[],
      tableData:[]
    }
  },
  created () {
    this.$axios.get('https://www.apiopen.top/journalismApi').then(res=>{
        // console.log(res.data.data.toutiao)
        //原生的表格
        this.datas = res.data.data.toutiao
        //element的表格
        this.tableData = res.data.data.toutiao
        console.log(this.tableData)

        //原生的ul
        this.items = res.data.data.toutiao
      }).catch(err=>{
        console.log(err)
      })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>

```
在调接口那插一杠子：**可以全局配置接口的基路径**
在min.js中接着写下如下 一行代码：
```
 axios.defaults.baseURL = 'http://https://www.apiopen.top/';
```
那么在**调接口时**，接口路径就只写`journalismApi`就可以了


---

一次性并发多个请求:

```javascript
	function getOne(){ 
		return axios.get('/user/12345',{ params:{ ID:12345，name:quanyi } });
	 } 
	function getTwos(){ 
		return axios.post('/user/12345/permissions',{
			id:"1"
		}); 
	} 
	
	axios.all([getOne(),getTwo()])
	.then(axios.spread(function(acct,perms){ 
		//当两个请求都完成的时候会触发这个函数，两个参数分别代表返回的结果
	 })
	).catch(function(err){
		console.log(err);
	});
```

axios可以通过配置config来发送请求:

```javascript
axios({
   	 method:"POST",
     url:'/user/12345',
   	 data:{
      	 firstName:"Fred",
       	lastName:"Flintstone"
   	 }
	}).then(function(res){
		console.log(res);
	}).catch(function(err){
		console.log(err);
});
```

----
**延申：**
jquery的ajsx请求：

```javascript
$.ajax({
   type: 'POST',
   url: url,
   data: data,
   dataType: dataType,
   success: function (res) {
	console.log(res);
	},
   error: function (err) {
	console.log(err);
	}
})
```
