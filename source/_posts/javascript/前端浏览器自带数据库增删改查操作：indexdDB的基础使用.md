---
title: 前端浏览器自带数据库增删改查操作：indexdDB的基础使用

index_img: https://img-blog.csdnimg.cn/37222ab31557452d8dabb843d5d1e2f7.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript
- 前端大存储
- indexedDB


---












![](https://img-blog.csdnimg.cn/37222ab31557452d8dabb843d5d1e2f7.gif#pic_center)


```html
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8">
		<meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0">
		<title>indexedDB</title>
		<link href="./favicon.png">
	</head>

	<body>
		<button onclick="addDataing()">增</button>
		<button onclick="deleteDBing()">删</button>
		<button onclick="updateDBing()">改</button>
		<button onclick="getDataByKeying()">查</button>
	</body>


	<script>
		var dbName = 'helloIndexDB',
			version = 1,
			storeName = 'helloStore',
			db;



		function openDB() {
			const request = window.indexedDB.open(dbName, version)
			request.onsuccess = function(event) {
				db = event.target.result // 数据库对象
				console.log('数据库打开成功')
			}

			request.onerror = function(event) {
				console.log('数据库打开报错')
			}

			request.onupgradeneeded = function(event) {
				// 数据库创建或升级的时候会触发
				console.log('据库创建/升级成功')
				db = event.target.result // 数据库对象
				let objectStore
				if (!db.objectStoreNames.contains(storeName)) {
					objectStore = db.createObjectStore(storeName, {
						keyPath: 'id'
					}) // 创建表
					// objectStore.createIndex('name', 'name', { unique: true }) // 创建索引 可以让你搜索任意字段
				}
			}
		}

		openDB();


		// 添加数据
		function addData(db, storeName, data) {
			let request = db.transaction([storeName], 'readwrite') // 事务对象 指定表格名称和操作模式（"只读"或"读写"）
			.objectStore(storeName) // 仓库对象
			.add(data)

			request.onsuccess = function(event) {
				console.log('数据写入成功')
			}

			request.onerror = function(event) {
				console.log('数据写入失败')
				throw new Error(event.target.error)
			}
		}

		// 根据id获取数据
		function getDataByKey(db, storeName, key) {
			let transaction = db.transaction([storeName]) // 事务
			let objectStore = transaction.objectStore(storeName) // 仓库对象
			let request = objectStore.get(key)

			request.onerror = function(event) {
				console.log('事务失败')
			}

			request.onsuccess = function(event) {
				console.log('主键查询结果: ', request.result)
			}
		}

		// 根据id修改数
		function updateDB(db, storeName, data) {
			let request = db.transaction([storeName], 'readwrite') // 事务对象
			.objectStore(storeName) // 仓库对象
			.put(data)

			request.onsuccess = function() {
				console.log('数据更新成功')
			}

			request.onerror = function() {
				console.log('数据更新失败')
			}
		}

		// 根据id删除数据
		function deleteDB(db, storeName, id) {
			let request = db.transaction([storeName], 'readwrite').objectStore(storeName).delete(id)

			request.onsuccess = function() {
				console.log('数据删除成功')
			}

			request.onerror = function() {
				console.log('数据删除失败')
			}
		}





		/* ========================================== */
		function addDataing() {
			addData(db, storeName, {
				id: (new Date().getTime()).toString(), // 必须且值唯一
				name: '张三',
				age: 18,
				desc: 'helloWord'
			})
		}


		function deleteDBing() {
			let id = prompt("请输入删除的id：");
			if (id === null || id === "") {
				return alert("请输入id");
			}
			deleteDB(db, storeName, id)
		}

		function updateDBing() {
			let id = prompt("请输入修改的id：");
			if (id === null || id === "") {
				return alert("请输入id");
			}
			updateDB(db, storeName, {
				id,
				name: '张三',
				age: 20,
				desc: '修改的内容'
			})
		}

		function getDataByKeying() {
			let id = prompt("请输入获取的id：");
			if (id === null || id === "") {
				return alert("请输入id");
			}
			getDataByKey(db, storeName, id)
		}
	</script>
</html>

```

