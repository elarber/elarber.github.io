---
title: js 选项卡 Tab切换

index_img: https://img-blog.csdnimg.cn/2019101300022520.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---












**首先引入bootstrap3哦**
**html：**
```html
<div id="case">
      <div class="container">
        <div class="title text-center" style="margin-bottom: 40px;">
          <h1>合作案例</h1>
          <div class="title-icon">
            <span class="before">———</span>
            <i class="angle down icon"></i>
            <span class="after">———</span>
          </div>
        </div>
        <div class="row text-center case-nav">
          <span class="col-xs-4 col-sm-2 col-md-2 active">查看全部</span>
          <span class="col-xs-4 col-sm-2 col-md-2">VI视觉</span>
          <span class="col-xs-4 col-sm-2 col-md-2">品牌全案</span>
          <span class="col-xs-4 col-sm-2 col-md-2">品牌官网</span>
          <span class="col-xs-4 col-sm-2 col-md-2">定制开发</span>
          <span class="col-xs-4 col-sm-2 col-md-2">宣传推广</span>
        </div>
        <div class="content">
          <div class="row all">
            <div class="col-xs-12 col-sm-6 col-md-3 all">111111111111111111111</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">111111111111111111111</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">111111111111111111111</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">111111111111111111111</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">111111111111111111111</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">111111111111111111111</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">111111111111111111111</div>
          </div>
          <div class="row vi">
            <div class="col-xs-12 col-sm-6 col-md-3 all">22222222222222222222</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">22222222222222222222</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">22222222222222222222</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">22222222222222222222</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">2222222222222222</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">22222222222222222222</div>
          </div>
          <div class="row brand">
            <div class="col-xs-12 col-sm-6 col-md-3 all">3333333333333333333</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">3333333333333333333</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">3333333333333333333</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">3333333333333333333</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">3333333333333333333</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">3333333333333333333</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">3333333333333333333</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">3333333333333333333</div>
          </div>
          <div class="row official">
              <div class="col-xs-12 col-sm-6 col-md-3 all">44444444444444444444</div>
              <div class="col-xs-12 col-sm-6 col-md-3 all">44444444444444444444</div>
              <div class="col-xs-12 col-sm-6 col-md-3 all">44444444444444444444</div>
              <div class="col-xs-12 col-sm-6 col-md-3 all">44444444444444444444</div>
              <div class="col-xs-12 col-sm-6 col-md-3 all">44444444444444444444</div>
              <div class="col-xs-12 col-sm-6 col-md-3 all">44444444444444444444</div>
              <div class="col-xs-12 col-sm-6 col-md-3 all">44444444444444444444</div>
              <div class="col-xs-12 col-sm-6 col-md-3 all">44444444444444444444</div>
          </div>
          <div class="row customized">
            <div class="col-xs-12 col-sm-6 col-md-3 all">555555555555555555555</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">555555555555555555555</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">555555555555555555555</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">555555555555555555555</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">555555555555555555555</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">555555555555555555555</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">555555555555555555555</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">555555555555555555555</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">555555555555555555555</div>
          </div>
          <div class="row extension">
            <div class="col-xs-12 col-sm-6 col-md-3 all">6666666666666666</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">6666666666666666</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">6666666666666666</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">6666666666666666</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">6666666666666666</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">6666666666666666</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">6666666666666666</div>
            <div class="col-xs-12 col-sm-6 col-md-3 all">6666666666666666</div>
          </div>
        </div>
      </div>
    </div>
```

**css：**

```css
  #case .case-nav {
    margin: 0 0 30px;
  }
  #case .case-nav span{
    padding: 12px 0;
    border-bottom: 1px solid #f3615a;
  }
  #case .case-nav span:hover {
    cursor: pointer;
    color: #f3615a;
  }
  #case .case-nav .active{
    border-bottom: none;
    border-top: 1px solid #f3615a;
    border-left: 1px solid #f3615a;
    border-right: 1px solid #f3615a;
    border-radius: 5px;
  }
  #case .vi,
  #case .brand,
  #case .official,
  #case .customized,
  #case .extension{
    display: none;
  }
```

**js：**

```javascript
var CaseNav = document.getElementsByClassName('case-nav')[0].getElementsByTagName('span');
var Content = document.getElementsByClassName('content')[0].getElementsByClassName('row');
  
for(let i=0; i<CaseNav.length; i++){
	CaseNav[i].onclick = ()=>{
		Content[i].style.display = 'block';
	  	CaseNav[i].classList.add("active");
	  	// 遍历所有的Content，让其都隐藏
	  	for(let j=0; j<Content.length; j++){
	    	Content[j].style.display = 'none';
	    	CaseNav[j]..classList.remove("active");
	  	}
	}
}
```
效果：
![](https://img-blog.csdnimg.cn/2019101300022520.gif)

