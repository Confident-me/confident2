#实例-楼层跳转

##知识点
####函数传参

`$(window).height();` //获取可视区域的高度

`$(document).height();`//获取整个页面的高度。

`offsetTop` //被选元素到可视区域顶部的距离。

事件绑定 委托
```javascript
$('.div1').on('click','li',function(){}
```

`hasClass` //检测当前元素是否含有某个特定的类

`index()` //搜索匹配的元素，并返回当前元素的索引值，从0开始计数。

`animate(1，2，3，4)`自定义动画函数，1 代表动画的参数比如：宽，高{"width":200,"height":"10%"}  2 代表动画的速度如：`“slow”/"normal"`或设置毫秒数  3 代表过度效果的名称如：`"linear" 或"swing"`使用更多需要插件  4 代表动画完成时要执行的函数

##实例代码
`html`
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>楼层跳转</title>
	<link rel="stylesheet" href="css/index.css">
	<script src="../jquery-3.1.1.min.js"></script>
</head>
<body>
	<div  class="dingbu"><input type="text" placeholder="搜索您想要的……"></div>
	<div class="content">
		<div class="banner">banner</div>
		<ul class="louceng">
			<li>
				<img src="images/1.jpg" alt="1楼" title="1楼">
			</li>
			<li>
				<img src="images/2.jpg" alt="2楼" title="2楼">
			</li>
			<li>
				<img src="images/3.jpg" alt="3楼" title="3楼">
			</li>
			<li>
				<img src="images/4.jpg" alt="4楼" title="4楼">
			</li>
			<li>
				<img src="images/5.jpg" alt="5楼" title="5楼">
			</li>
			<li>
				<img src="images/6.jpg" alt="6楼" title="6楼">
			</li>
			<li>
				<img src="images/7.jpg" alt="7楼" title="7楼">
			</li>
			<li>
				<img src="images/8.jpg" alt="8楼" title="8楼">
			</li>
		</ul>
	</div>

	<div class="div1">
		<ul>
			<li>1</li>
			<li>2</li>
			<li>3</li>
			<li>4</li>
			<li>5</li>
			<li>6</li>
			<li>7</li>
			<li>8</li>
			<li class="last">∧</li>
		</ul>

	</div>
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
body{
	height: 3000px;
}
.dingbu{
	width: 100%;
	height: 50px;
	border: 1px solid black;
	text-align: center;
	line-height: 45px;
	position: fixed;
	top:-8%;
	background: rgba(0,0,0,0.3);
}
.dingbu input{
	width: 40%;
	height: 25px;
	outline: none;
	font-size: 14px;
	color: #333;
}
.div1{
	width: 30px;
	/*border: 2px solid red;*/
	color: black;
	position: fixed;
	bottom: 10%;
	right: -7%;
}
.div1 li{
	border: 1px solid black;
	text-align: center;
	font-size: 20px;
	line-height: 30px;
	height: 30px;
	cursor: pointer;
}
.div1 li:hover{
	background: red;
}
.content{
	margin: 0 auto;
	width: 70%;
	margin-top: 50px;
}
.banner{
	width: 100%;
	height: 300px;
	border: 1px solid black;
	text-align: center;
	line-height: 300px;
	font-size: 30px;
}
.louceng li{
	width: 100%;
	height: 500px;
	border: 1px solid red;
	margin: 5px 0;
	text-align: center;
	line-height: 300px;
	font-size: 30px;
}
.louceng li img{
	width: 100%;
	height: 100%;
}
```
`javascript`
```javascript
$(function(){
	var btn = $(".div1 li");
	var louceng = $(".louceng li");
	var statusT = true;
	var statusB = true;
	//初始化
	function init(){
		if(st>200){
			if (statusT) {
				show(0,"3%");
				statusT = false;
				statusB = true;
			};
		}else{
			if (statusB) {
				show("-8%","-7%");
				statusT = true;
				statusB = false;
			};
		}
	}
	init();
/*
* 动画
* @parm _top【number/string】 顶部的偏移  
* @parm _right【string】 	侧边栏侧边的偏移
*/
	function show(_top,_right){
		//顶部
		$(".dingbu").stop().animate({top:_top},500);
		//侧边栏
		$(".div1").stop().animate({right:_right},500)
	}
	var st = $(document).scrollTop();
	//根据滚动条和中间内容 改变右侧楼层的样式
	function louBtn(){
		var wh = $(window).height();//可视区域的高度
		for(var i = 0;i<louceng.length;i++){
			var lcTop = louceng[i].offsetTop;
			if(lcTop<st+wh/2-200){
				for(var j = 0;j<btn.length;j++){
					btn[j].style.color = "black";
					btn[j].style.background = "#fff";
				}
				btn[i].style.color = "#fff";
				btn[i].style.background = "black";
			}
		}
	}
	louBtn();


	$(window).scroll(function(){
		st = $(document).scrollTop();
		init();
		louBtn();
	});

	//侧边栏点击
	$('.div1').on('click','li',function(){
		var $this =$(this);
		var _index = $('.div1').find('li').index(this);
		var _top = 0;
		// console.log(_index);
		if(!$this.hasClass('last')){
			_top = $(".louceng li").eq(_index).offset().top
		}
		$("html,body").stop().animate({"scrollTop":_top-60},500);
	});

})
/**
* _index 是点击的当前的侧边栏的按钮的下标
* _top  是高度 初始化是0
* _top = $(".louceng li").eq(_index).offset().top 
* 这句话的意思是把点击侧边栏按钮的下标赋值给楼层相对应的下标，在获取当前楼层到页面（document）顶部的距离
* $("html,body").stop().animate({"scrollTop":_top-60},500);
* 然后在赋值给滚动条
*/
```




