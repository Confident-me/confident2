#实例-鼠标滑过图片放大有遮罩

##事件委托函数示例
####on方法第一个参数是事件类型（click/mouseenter...），第二个参数是`子元素`，fn
```javascript
$(".ul1").on("mouseenter mouseleave","li",function(e){
	if(e.type == "mouseenter"){
		//执行的代码
	}
	else{
		//执行的代码
	}
	
}
```
####通过上面这个例子，说明on函数的第一个参数是可以传多个事件类型的，比如：`mouseenter`,`mouseleave`,鼠标指针穿过元素时，或鼠标指针离开元素时所要执行的函数。
`find()`;是查找当前匹配元素的后代元素。
```javscript
$("#div1").find("span")
```
##实例：鼠标划过，图片放大，有遮罩效果。
####``html:``
```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>hover图片放大效果</title>
    <link rel="stylesheet" href="css/index.css">
    <script src="../jquery-3.1.1.min.js"></script>
</head>
<body>
	<ul class="ul1">
		<li class="slide">
			<img src="images/1.jpg" alt="">
		</li>
		<li class="slide">
			<img src="images/2.jpg" alt="">
		</li>
		<li class="slide">
			<img src="images/3.jpg" alt="">
		</li>
		<li class="slide">
			<img src="images/4.jpg" alt="">
		</li>
		
	</ul>
</body>
<script src="js/index.js"></script>
</html>
```
####`css:`
```css
*{
	margin: 0;
	padding: 0;
	list-style: none;
}
.ul1{
	width: 90%;
	height: 500px;
	border: 1px solid black;
	margin: 50px auto;
	position: relative;
}
.slide{
	width: 48%;
	height: 48%;
	float: left;
	margin: 5px;
	position: relative;
	overflow: hidden;
}
.slide img{
	display: block;
	width: 100%;
	height: 100%;
	z-index: 1;
}
.showHid{
	width: 100%;
	height: 100%;
	background: rgba(0,0,0,0.3);
	position: absolute;
	z-index: 5;
	top: 0;
	left: 0;
}
```
####`javascript`
```javascript
$(function(){
    var imgWid = 0;
    var imgHei = 0;
    var big = 1.1;
    $(".ul1").on("mouseenter mouseleave","li",function(e){
        var $img = $(this).find('img');
        var divs = "<div class='showHid'></div>";
        imgWid = $img.width();
        imgHei = $img.height();
        var imgWid2 = imgWid * big;
        var imgHei2 = imgHei * big;
        var obj = null;
        if(e.type == 'mouseenter'){
            obj = {"width":imgWid2,"height":imgHei2,"margin-top":-(imgHei2-imgHei)/2,"margin-left":-(imgWid2-imgWid)/2};
            $img.after(divs)
        }else{
            obj = {"width":"100%","height":"100%","margin-top":0,"margin-left":0};
            $(this).find('div').remove()
        }
        $img.stop().animate(obj);
    })

})
```
