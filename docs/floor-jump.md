#实例-楼层跳转

##知识点
####函数传参
####`$(window).height();`//获取可视区域的高度
####`$(document).height();`//获取整个页面的高度。
####`offsetTop` //被选元素到可视区域顶部的距离。
####事件绑定 委托
####`hasClass` //检测当前元素是否含有某个特定的类
####`index()` //搜索匹配的元素，并返回当前元素的索引值，从0开始计数。
```html
<ul>
  <li id="foo">foo</li>
  <li id="bar">bar</li>
  <li id="baz">baz</li>
</ul>
```
```javascript
$('li').index(document.getElementById('bar')); //1，传递一个DOM对象，返回这个对象在原先集合中的索引位置
$('li').index($('#bar')); //1，传递一个jQuery对象
$('li').index($('li:gt(0)')); //1，传递一组jQuery对象，返回这个对象中第一个元素在原先集合中的索引位置
$('#bar').index('li'); //1，传递一个选择器，返回#bar在所有li中的索引位置
$('#bar').index(); //1，不传递参数，返回这个元素在同辈中的索引位置。  
```
####`animate()`