---
title: 使用node建立http接口请求

index_img: https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240412003349610.png
lazyload: true
categories:
- node
tags:
- node



---











# 编写接口

```javascript
const express = require('express');
const app = express();

const cors = require('cors');
app.use(cors());

const bodyParser = require('body-parser');
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: false }));
 

/* const mysql = require('mysql');
const conn = mysql.createConnection({
    host: 'localhost',
    user: 'root',
    password: '123456',
    database: 'test',
    multipleStatements: true
})
conn.connect(); */
 

app.listen(8080, () => {
    console.log('——————————服务已启动——————————');
})
 
/* app.get('/', (req, res) => {
    res.send('<h1 style="color:red">服务已启动</h1>');
}) */
 
app.get('/api/getData', (req, res) => {
    /* const sqlStr = 'SELECT * FROM users'
    conn.query(sqlStr, (error, results) => {
        if (error) return res.json({ code: 10001, message: error})
        res.json({ code: 10000, message: results})
    }) */
    res.json({ code: 10000, message: {aaa:1,bbb:2}})
})
```



# 前端调用

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>调用node接口</title>
    <script src="https://cdn.bootcss.com/jquery/3.4.1/jquery.min.js"></script>
</head>
<body>
    <button onclick="getData()">获取</button>
</body>
<script>
			function getData(){
				fetch("http://localhost:8080/api/getData").then(res=>{
					return res.json()
				}).then(res=>{
					console.log(res);
				})
			}
		</script>
</html>
```





# 效果

![](https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240412003100368.png)



![](https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240412003349610.png)
