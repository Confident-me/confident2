#提示框(当提示框小于页面的高度会在上面显示)

##思想：
1. 先获取当前要显示的元素的Y轴的坐标 `ev.pageY`;
2. 在获取自身的高度，`$("选择器").height()`;
3. 然后在获取滚动条的高度，`$(document).scrollTop()`;
4. 在获取可视区域的的高度，`$(window).height()`;
5. 然后判断if(1+2 > 3+4){那就说明要显示的盒子会超过window的页面，就让盒子显示到上面};
6. else{就让盒子显示在下面};

##实例代码
`html`
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>提示框弹窗</title>
	<link rel="stylesheet" href="assetsCss/index.css">
</head>
<body>
	<div class="box">
		<ul class="bg_box">
			<div class="jewel">
				滑上来试试
			</div>

			<ul class="list">
				<li>提示框</li>
			</ul>
		</ul>
		<ul class="bg_box">
			<div class="jewel">
				滑上来试试
			</div>

			<ul class="list">
				<li>提示框</li>
			</ul>
		</ul>
		<ul class="bg_box">
			<div class="jewel">
				滑上来试试
			</div>

			<ul class="list">
				<li>提示框</li>
			</ul>
		</ul>
		<ul class="bg_box">
			<div class="jewel">
				滑上来试试
			</div>

			<ul class="list">
				<li>提示框</li>
			</ul>
		</ul
	</div>
	
</body>
<script src="assetsScript/jquery-3.1.1.min.js"></script>
<script src="assetsScript/index.js"></script>
</html>
```
`css`
```css
*{
	padding: 0;
	margin: 0;
	list-style: none;
}
.box{
	width: 100%;
	border: 1px solid black;
	width: 50%;
	margin: 0 auto;
}
.bg_box{
	width: 30%;
	height: 300px;
	margin: 0px auto;
	position: relative;

}
.jewel{
	border-radius: 50%;
	width: 100px;
	height: 100px;
	background: navajowhite;
	margin: 0 auto;
	text-align: center;
	line-height: 100px;
}
.list{
	width: 100px;
	height: 200px;
	display: none;
	position: absolute;
	left: 0;
	right: 0;
	margin: auto;
	border-radius: 10px;
}
.list li{
	background: mediumvioletred;
	width: 100%;
	height: 100%;
	text-align: center;
	line-height: 200px;
	color: snow;
	border-radius: 10px;
}
```
`javascript`
```javascript
$(function(){
	$(".bg_box").on("mouseenter mouseleave","div",function(ev){
		var that = $(this);
		function scro(){
			that.siblings().show();
			var ev_y = ev.pageY;
			var listHei = $(".list").height();
			var winSco = $(document).scrollTop();
			var winHei = $(window).height();
			if (ev_y + listHei > winSco+winHei) {
				that.siblings().css({"bottom":"300px"});
			}else{
				that.siblings().css({"bottom":0});
			}
		};
		if (ev.type == "mouseenter") {
			scro();
		}else{
			that.siblings().hide();
		};
	});

});
```










