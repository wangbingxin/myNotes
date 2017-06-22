## SPA(Single Page Application,单页面应用)

单页应用的优缺点：

	优点：
		1. 前后端分离
		2. 减轻服务器压力
		3. 用户体验良好，页面切换不需要重新加载整个页面
	缺点：
		1. SEO不友好
		2. 首次加载过于庞大，耗时较多，宽带要求高
		3. 历史记录较难管理

### 实现单页面的两种方式：HTML5 history API和location.hash

#### history API

HTML4 history API的属性方法：

	history.length:历史记录中的地址个数
	history.back():后退
	history.forward():前进
	history.go(n):在历史记录范围内去到一个指定的地址

HTML5的history API新增了两个方法，一个属性，一个事件

一属性

	history.state:获取历史栈中最顶端的state数据

两方法：

	在历史记录中添加记录
	history.pushState(state, title, url);

	替换当前记录
	history.replaceState(state, title, url);

	
1. state:存储JSON字符串，地址切换时可以跟着走
2. title:字符串，代表当前页面的标题，可以忽略该参数，null
3. url:字符串，用于更新浏览器的地址栏，但不会重新加载页面

一事件:
	
	当用户点击浏览器的「前进」、「后退」按钮时，就会触发popstate事件.
	以上两个方法的state参数此时就起到作用了！
	window.addEventListener("popstate", function(e) {
	    var state = e.state;
	    // do something...
	});

#### location.hash

获取当前地址的hash值
	```
	location.hash
	```
	
`hash值`变化时会触发事件

	window.addEventListener("hashchange", function(e) {
	    // do something...
	});