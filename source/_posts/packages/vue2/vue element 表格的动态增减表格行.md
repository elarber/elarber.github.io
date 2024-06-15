---
title: vue element 表格的动态增减表格行

index_img: https://img-blog.csdnimg.cn/20210224132619745.gif
lazyload: true
categories:
- vue2
- 拿来主义
tags:
- vue2
- vue
- elementUI

---









![](https://img-blog.csdnimg.cn/20210224132619745.gif#pic_center)


#### html：
```html
<el-table size="mini" :data="eventSetings">
   <el-table-column label="消费金额">
     <template slot-scope="scope">
       <el-input v-model="scope.row.money" size="mini" />
     </template>
   </el-table-column>
   <el-table-column label="减免金额">
     <template slot-scope="scope">
       <el-input v-model="scope.row.reduce" size="mini" />
     </template>
   </el-table-column>
   <el-table-column align="right">
     <template slot="header" slot-scope="scope">
       <el-button type="primary" @click="addEventSet">添 加</el-button>
     </template>
     <template slot-scope="scope">
       <el-button
         size="mini"
         type="danger"
         @click="deleteEventSet(scope.$index, scope.row)"
         >删除</el-button
       >
     </template>
   </el-table-column>
 </el-table>
```

#### js：

```javascript
// 数据部分
eventSetings: [
  {
    money: "",
    reduce: "",
  },
]





// 逻辑部分
// 添加
addEventSet() {
   this.eventSetings.push({
     money: "",
     reduce: "",
   });
 },
 // 删除
 deleteEventSet(index, data) {
   console.log(index, data);
   this.eventSetings.splice(index, 1);
 },
```




