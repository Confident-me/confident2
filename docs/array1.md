#数组去重
##用字典的方法实现数组去重
```javascript

Array.prototype.quchong = function(){
  //先创建一个空数组
  var r = [];
  // 创建一个空对象
  var dict = {};
  for (var i = 0; i < this.length; i++) {
    if (!dict[this[i]]) {//如果字典里没有重复的数字
      r.push(this[i]);
      dict[this[i]] = true;
    };
  };
  return r;
}
  var arr = [13,4,5,35,66,77,4,12,11,11,35]
  alert(arr.quchong());

```
####思路
此方法是写在数组的原型链上的，
>1. 首先我们先创建一个空的数组用来存储新的数组
>2. 然后我们在建一个空字典（必须是一个对象{}，或者数组[] ）。
>3. 然后我们循环 调用的那个数组。
>4. 判断如果字典里有没有这个数字，如果没有，push到 r新数组。
