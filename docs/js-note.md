#js笔记

##第一个demo 鼠标移入移出 (提示框)
```html
<div type="checkbox" onmousemove="divShow()" onmouseout="divHid()">鼠标移入移出</div>
<div id="div1">
    为了您的安全，请不要……
</div>
```
```css
#div1{
    width:100px;
    height:50px;
    background: #ccc;
    display: none;
}
```
```javascript
 window.onload = function(){
	var div1 = document.getElementById("div1");
	divShow = function (){
		div1.style.display = 'block';
	}
	divHid = function (){
		div1.style.display = 'none';
	}
}
```
##函数传参 
####当函数里有一部分东西确定不下来的时候用参数
####demo1  点击改变背景颜色
```javascript
// css
#div1{
    width:200px;
    height:200px;
    background: red;
}

//html
<input type="button" value="变绿" onclick="setColor('green')">
<input type="button" value="变黄" onclick="setColor('yellow')">
<input type="button" value="变黑" onclick="setColor('black')">
<div id="div1"></div>

//javascript
function setColor(color){
	var div1 = document.getElementById("div1");
	div1.style.background = color;
}
```

操作属性的方法：
1. 对象.属性 = “值”  例：

```javascript
function setStyle(){
	div.className = "abc";
}

```
2. 对象['属性'] = “值” 例：

```javascript
function setStyle(name){
	//div['className'] = 'abc';
	/*var aa = alcssName;
	div[aa] = "abc";*/
	div[name] = "abc";
}

```
这个方法有个好处，就是可以用`变量`,或者`字符串`代替，也就可以接受`参数`
####demo2
```javascript
//html
<input type="button" value="变绿" onclick="setColor('background','green')">
<input type="button" value="变黄" onclick="setColor('width','500px')">
<input type="button" value="变黑" onclick="setColor('height','500px')">
<div id="div1"></div>

//javascript
 function setColor( name,color){
	var div1 = document.getElementById("div1");
	div1.style[name] = color;
}
```
##循环
####`demo1`全选/不选/反选
```javascript
//html
input id="btn1" type="button" value="全选">
<input id="btn2" type="button" value="不选">
<input id="btn3" type="button" value="反选">
<div id="div1">
    <input type="checkbox" value="选择"><br>
    <input type="checkbox" value="选择"><br>
    <input type="checkbox" value="选择"><br>
    <input type="checkbox" value="选择"><br>
    <input type="checkbox" value="选择"><br>
</div>

//javascript
window.onload = function(){
    var oBtn1 = document.getElementById('btn1');
    var oBtn2 = document.getElementById('btn2');
    var oBtn3 = document.getElementById('btn3');
    var div1 = document.getElementById('div1');
    var aCh = div1.getElementsByTagName('input');
    oBtn1.onclick = function(){
        for(var i = 0;i<aCh.length;i++){
            aCh[i].checked = true;
        }
    }
    oBtn2.onclick = function(){
        for(var i = 0;i<aCh.length;i++){
            aCh[i].checked = false;
        }
    }
    oBtn3.onclick = function(){
        for(var i = 0;i<aCh.length;i++){
            if(aCh[i].checked == false){
                aCh[i].checked = true;
            }else{
                aCh[i].checked = false;
            }
        }
    }
}
```




























