# <center><font face="微软雅黑">AJAX
2018/6/29 15:33:06 

## 什么是AJAX

Ajax = 异步JavaScript和xml。

Ajax是一种用于创建快速动态网页的技术。

通过在后台与服务器进行少量数据交换，AJAX 可以使网页实现异步更新。这意味着可以在不重新加载整个网页的情况下，对网页的某部分进行更新。

传统的网页（不使用 AJAX）如果需要更新内容，必需重载整个网页面。

##创建XMLHttpRequest对象

XMLHttpRequest 用于在后台与服务器交换数据。这意味着可以在不重新加载整个网页的情况下，对网页的某部分进行更新。

    let xhr = new XMLHttpRequest();

##向服务器发送请求请求

如需将请求发送到服务器，我们使用 XMLHttpRequest 对象的 open() 和 send() 方法：

    xhr.open(method,url,async)

    xhr.send(string)

- method:请求的类型；GET 或 POST
- url:文件在服务器上的位置
- async:true（异步）或 false（同步)
- string:仅用于 POST 请求,将请求发送到服务器。

##服务器响应

如需获得来自服务器的响应，请使用 XMLHttpRequest 对象的 responseText 或 responseXML 属性。

    responseText   获得字符串形式的响应数据
    responseXML	   获得 XML 形式的响应数据

##onreadystatechange 事件

当请求被发送到服务器时，我们需要执行一些基于响应的任务。

每当 readyState 改变时，就会触发 onreadystatechange 事件

readyState 属性存有 XMLHttpRequest 的状态信息。

- onreadystatechange:  存储函数（或函数名），每当 readyState 属性改变时，就会调用该函数。
- readyState:  存有 XMLHttpRequest 的状态。从 0 到 4 发生变化。

&emsp;&emsp;&emsp;&emsp;&emsp;0: 请求未初始化

&emsp;&emsp;&emsp;&emsp;&emsp;1: 服务器连接已建立

&emsp;&emsp;&emsp;&emsp;&emsp;2: 请求已接收

&emsp;&emsp;&emsp;&emsp;&emsp;3: 请求处理中

&emsp;&emsp;&emsp;&emsp;&emsp;4: 请求已完成，且响应已就绪

- status:  
&emsp;&emsp;&emsp;&emsp;200: "OK",  
&emsp;&emsp;&emsp;&emsp;404: 未找到页面

实例

    xhr.onreadystatechange=function()
	{
    	if (xhr.readyState==4 && xhr.status==200)
    	{
        	document.getElementById("div").innerHTML=xhr.responseText;
    	}
	}

##完整版使用回调函数
回调函数是一种以参数形式传递给另一个函数的函数。

如果您的网站上存在多个 AJAX 任务，那么您应该为创建 XMLHttpRequest 对象编写一个标准的函数，并为每个 AJAX 任务调用该函数。

该函数调用应该包含 URL 以及发生 onreadystatechange 事件时执行的任务（每次调用可能不尽相同):

    function loadXMLDoc (url, cfunc){
		let xhr = new XMLHttpRequest();
		xhr.onreadystatechange = cfunc;
		xhr.open("GET",url,true);
		xhr.send();
	}
	function myFunction() {
	loadXMLDoc("ajax.txt",function() {
		if(xhr.readyState ==4 && xhr.status==200){
			document.getElementById("div").innerHTML=xhr.responseText;
		}
	)}

