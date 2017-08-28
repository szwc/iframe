# iframe 页面之间的交互

脚本试图访问的框架内容必须遵守同源策略(也就意味着需采用http协议)，并且无法访问非同源的window对象的几乎所有属性。同源策略同样适用于子窗体访问父窗体的window对象

## 父访问子

（需等待iframe加载完才能访问到属性）通过contentWindow属性，脚本可以访问iframe元素所包含的HTML页面的window对象。contentDocument属性则引用了iframe中的文档元素（等同于使用contentWindow.document），但IE8-不支持

## 子访问父

通过访问window.parent，脚本可以从框架中引用它的父框架的window。

## window.name 跨域

原理：同一个窗口，只要窗口不关闭，window.name也不会变

实现：例如：80端口下 a.html想获取到 3000端口下data.html的数据，可通过iframe加载 data.html,待iframe加载完后，将iframe的src指向同a同域的b.html，即可获得3000端口 data.html的window.name值
a页面代码
`
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>parent</title>
</head>
<body>
	<h1>这是父页面</h1>
	<br>
	<br>
	<iframe src="http://127.0.0.1:3000/data.html" frameborder="0" style="height:300px;width:300px;background-color:skyblue"></iframe>
	<script>
		
		//window.name 跨域
		var iframe = document.getElementsByTagName('iframe')[0];
		iframe.onload = function (){
			var thrwin = iframe.contentWindow;
			try{
				var data = thrwin.name;
				console.log(data);
			}catch(e){
				iframe.src="b.html";
				console.log(data);
			}
		}

		
	</script>
</body>
</html>
`
b页面代码
`
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>form</title>
</head>
<body>
	<script>
		window.name="3000 端口的window.name";
	</script>
</body>
</html>
`

## window.postMessage 跨域

[MDN | 官方文档](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/postMessage)

### 语法
`otherWindow.postMessage(message, targetOrigin, [transfer]);`

该方法会向目标窗口派发一个 MessageEvent消息，对方通过window的onmessage接收

`window.addEventListener("message", function(){}, false);`

使用Postmessage   安全是必须要考虑的



