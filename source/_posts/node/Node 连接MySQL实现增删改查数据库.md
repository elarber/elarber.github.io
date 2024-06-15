---
title: Node 连接MySQL实现增删改查数据库
index_img: https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240412105507103.png
lazyload: true
categories:
- node
tags:
- node



---












# 连接数据库

```javascript
const mysql = require('mysql');
const conn = mysql.createConnection({
    host: '127.0.0.1',
    user: 'root',
    password: '123456',
    database: 'test',
    port: '3306',      
    multipleStatements: true
})
conn.connect();
```



![](https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240412121920199.png)



![](https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240412121754458.png)









# 查询数据

```javascript
const express = require('express');
const app = express();

const cors = require('cors');
app.use(cors());

const bodyParser = require('body-parser');
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: false }));
 

const mysql = require('mysql');
const conn = mysql.createConnection({
    host: '127.0.0.1',
    user: 'root',
    password: '123456',
    database: 'test',
    port: '3306',      
    multipleStatements: true
})
conn.connect();
 

app.listen(8080, () => {
    console.log('——————————服务已启动——————————');
})
 
app.get('/', (req, res) => {
    res.send('<h1 style="color:red">服务已启动</h1>');
})
 
app.get('/api/getData', (req, res) => {
    const sqlStr = 'SELECT * FROM users'
    conn.query(sqlStr, (error, results) => {
        console.log(results);
        if (error) return res.json({ code: 10001, message: error})
        res.json({ code: 10000, message: results})
    })
})
```

![](https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240412105507103.png)





# 更新数据

```javascript
// 更新数据
app.get('/api/upData', (req, res) => {
    var modSql = `UPDATE users SET name = ?, age = ? WHERE id = 2`;
    conn.query(modSql, ['哈哈哈', 123, 2], (error, result) => {
        console.log(result);
        if (error) {
            console.log('[UPDATE ERROR] - ', error.message);
            return;
        }
        console.log('--------------------------UPDATE----------------------------');
        console.log('UPDATE affectedRows', result.affectedRows);
        console.log('-----------------------------------------------------------------\n\n');
    })

    conn.end(function (err) {
        res.json({ code: 200, message: "修改成功" })
    });
})
```



![](https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240412120527773.png)





# 插入数据



```javascript
	// 插入数据
app.get('/api/insertData', (req, res) => {
    const addSql = 'INSERT INTO users(name,age) VALUES(?,?)';
    const addSqlParams = ['陈欣', 122];
    conn.query(addSql, addSqlParams,(error, results) => {
        if (error) return res.json({ code: 10001, message: error })
        conn.end(function (err) {
            res.json({ code: 200, message: "新增成功" })
        });
    })
})
```



![](https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240412121447300.png)





# 删除数据

```javascript
// 删除数据
app.get('/api/deleteData', (req, res) => {
    const addSql = 'DELETE FROM users where id=3';
    conn.query(addSql,(error, results) => {
        if (error) return res.json({ code: 10001, message: error })
        conn.end(function (err) {
            res.json({ code: 200, message: "已删除" })
        });
    })
})
```





![](https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240412121711232.png)



