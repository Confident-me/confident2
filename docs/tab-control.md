#选项卡(5秒之内只能点一次)

##知识点：

1. index();

2. 事件委托；on("click","li",function(ev){});

3. attr();

4. timeStamp; 事件对象自己的一个属性 `时间戳`;


##实例代码
`html`
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>选项卡刷新</title>
	<link rel="stylesheet" href="css/index.css">
	<script src="../jquery-3.1.1.min.js"></script>
</head>
<body>
	<ul class="btns">
		<li class="back">1</li>
		<li>2</li>
		<li>3</li>
		<li>4</li>
	</ul>
	<ul class="cons">
		<li class="cengji">1</li>
		<li>2</li>
		<li>3</li>
		<li>4</li>
	</ul>
</body>
<script src="js/index2.js"></script>
</html>
```
`css`
```css
*{
	padding: 0;
	margin: 0;
	list-style: none;
}
.btns{
	width: 408px;
	overflow: hidden;
	margin: 0 auto;
	margin-top: 50px;
}
.btns li{
	width: 100px;
	height: 40px;
	border: 1px solid red;
	float: left;
	text-align: center;
	line-height: 40px;
	font-size: 30px;
}
.cons{
	width: 408px;
	height: 500px;
	border: 1px solid black;
	margin: 10px auto;
	position: relative;
}
.cons li{
	position: absolute;
	left: 0;
	top: 0;
	display: none;
	text-align: center;
	line-height: 500px;
	width: 100%;
	height: 100%;
	background: #ccc;
	color: #000;
	font-size: 50px;
}
.cons .cengji{
	display: block;
}
.back{
	background: palevioletred;
	color: #fffcd3;
}
```
`javascript`
```javascript
$(function(){
	var $btns = $(".btns"),
		$cons = $(".cons");

	$btns.on("click","li",function(ev){
		var $this = $(this);
		var _index = $btns.find('li').index(this);
		if(ev.timeStamp - Number($this.attr('data-time')) < 5000){
			return;
		};
		$this.attr('data-time',ev.timeStamp);
		var $cs = $cons.find('li').css('display','none').eq(_index).css('display','block');
	})
})
```








