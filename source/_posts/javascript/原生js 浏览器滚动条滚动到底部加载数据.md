---
title: 原生js 浏览器滚动条滚动到底部加载数据

index_img: https://img-blog.csdnimg.cn/20191218163337384.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---











![原生js 浏览器滚动条滚动到底部加载数据](https://img-blog.csdnimg.cn/20191218163337384.gif)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
  <style>
    <style>
    * {
      margin: 0;
      padding: 0;
    }
    #app {
      height: 500px;
      overflow-y: scroll;
    }
    ul {
      list-style: none;
    }
    li {
      background-color: yellowgreen;
      margin-top: 2px;
    }
    li:hover {
      background-color: deeppink;
    }
    .blank {
      height: 1px;
    }
    .lazy {
      text-align: center;
      display: none;
      background-color: deepskyblue;
    }
  </style>
  </style>
</head>
<body>
  <div id="app">
    <ul>
      <li>1</li>
      <li>2</li>
      <li>3</li>
      <li>4</li>
      <li>5</li>
      <li>6</li>
      <li>7</li>
      <li>8</li>
      <li>9</li>
      <li>10</li>
      <li>11</li>
      <li>12</li>
      <li>13</li>
      <li>14</li>
      <li>15</li>
      <li>16</li>
      <li>17</li>
      <li>18</li>
      <li>19</li>
      <li>20</li>
      <li>21</li>
      <li>22</li>
    </ul>
    <p class="blank"></p>
    <p class="lazy">懒加载中...</p>
  </div>


  <script>
    const app = document.querySelector('#app');
    const ul = app.querySelector('ul');
    const blank = app.querySelector('.blank');
    const lazyDom = app.querySelector('.lazy');
    const NUM = 10;

    function createDom() {
      const fragment = document.createDocumentFragment();
      console.log(fragment, 99);
      const maxNum = +ul.querySelector('li:last-of-type').innerText;
      console.log(maxNum + NUM, 777);
      for (let index = maxNum; index < maxNum + NUM;) {
        const dom = document.createElement('li');
        dom.innerText = ++index;
        fragment.appendChild(dom);
      }
      ul.appendChild(fragment);
    };

      const observer = new IntersectionObserver(entries => {
      if (entries[0].isIntersecting) {
        lazyDom.style.display = 'block';
        setTimeout(() => {
          createDom();
        }, 500);
      } else {
        lazyDom.style.display = 'none';
      }
    });
    observer.observe(blank);
  </script>
</body>
</html>
```


