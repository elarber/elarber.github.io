---
title: Node 事件循环

index_img: https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240412091809968.png
lazyload: true
categories:
- node
tags:
- node



---











# 回调函数

异步编程依托于回调来实现，但不能说使用了回调后程序就异步化了。

回调函数在完成任务后就会被调用，Node 使用了大量的回调函数，Node 所有 API 都支持回调函数。

例如，我们可以一边读取文件，一边执行其他命令，在文件读取完成后，我们将文件内容作为回调函数的参数返回。这样在执行代码时就没有阻塞或等待文件 I/O 操作。这就大大提高了 Node.js 的性能，可以处理大量的并发请求。

## 阻塞代码实例

```javascript
const fs = require("fs");

const data = fs.readFileSync('./input.txt');
console.log(data.toString());
console.log("程序执行结束!");
```



![](https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240412091650110.png)

## 非阻塞代码实例

```javascript
const fs = require("fs");

fs.readFile('input.txt', function (err, data) {
  if (err) return console.error(err);
  console.log(data.toString());
});

console.log("程序执行结束!");
```



![](https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240412091809968.png)



以上两个实例我们了解了阻塞与非阻塞调用的不同。第一个实例在文件读取完后才执行程序。 第二个实例我们不需要等待文件读取完，这样就可以在读取文件时同时执行接下来的代码，大大提高了程序的性能。

因此，阻塞是按顺序执行的，而非阻塞是不需要按顺序的，所以如果需要处理回调函数的参数，我们就需要写在回调函数内。





# 事件循环

> Node是单进程单线程应用程序，但是因为 V8 引擎提供的异步执行回调接口，通过这些接口可以处理大量的并发，所以性能非常高。单线程类似进入一个while(true)的事件循环，直到没有事件观察者退出，每个异步事件都生成一个事件观察者，如果有事件发生就调用该回调函数.

Node.js 使用事件驱动模型，当web server接收到请求，就把它关闭然后进行处理，然后去服务下一个web请求。当这个请求完成，它被放回处理队列，当到达队列开头，这个结果被返回给用户。这个模型非常高效可扩展性非常强，因为 webserver 一直接受请求而不等待任何读写操作。（这也称之为非阻塞式IO或者事件驱动IO）

在事件驱动模型中，会生成一个主循环来监听事件，当检测到事件时触发回调函数。

![](https://www.runoob.com/wp-content/uploads/2015/09/event_loop.jpg)



整个事件驱动的流程就是这么实现的，非常简洁。有点类似于观察者模式，事件相当于一个主题(Subject)，而所有注册到这个事件上的处理函数相当于观察者(Observer)。







# 实例

```javascript
const events = require('events');
const eventEmitter = new events.EventEmitter();

// 创建事件处理程序
const connectHandler = function connected() {
  console.log('连接成功。');

  eventEmitter.emit('data_received'); // 触发 data_received 事件 
}

// 绑定 connection 事件处理程序
eventEmitter.on('connection', connectHandler);
// 使用匿名函数绑定 data_received 事件
eventEmitter.on('data_received', function () {
  console.log('数据接收成功。');
});


eventEmitter.emit('connection');// 触发 connection 事件 

console.log("程序执行完毕。");
```







![](https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240412090834970.png)





