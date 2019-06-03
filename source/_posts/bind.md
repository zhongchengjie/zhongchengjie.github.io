---
title: call、apply和bind使用
date: 2017-10-26 22:44:06
tags:
 - call
 - apply
 - bind
categories: javascript
---

##### call和apply
+ obj.call(thisObj, arg1, arg2, ...);
+ obj.apply(thisObj, [arg1, arg2, ...]);

两者作用一致，都是把obj(即this)绑定到thisObj，这时候thisObj具备了obj的属性和方法。或者说thisObj继承了obj的属性和方法。绑定后会立即执行函数。**唯一区别是apply接受的是数组参数，call接受的是连续参数**。
````javascript
function add(j, k){
    return j+k;
}
function sub(j, k){
    return j-k;
}

add(5,3); //8
add.call(sub, 5, 3); //8
add.apply(sub, [5, 3]); //8

sub(5, 3); //2
sub.call(add, 5, 3); //2
sub.apply(add, [5, 3]); //2
````

##### 调用原生对象的方法
示例：
````javascript
var a = {0:1, 1:"yjc", length: 2};
a.slice(); //TypeError: a.slice is not a function
Array.prototype.slice.call(a);//[1, "yjc"]
````
对象a类似array，但不具备array的slice等方法。使用call绑定，这时候就可以调用slice方法。

##### 实现继承
通过call和apply，我们可以实现对象继承。示例：
````javascript
var Parent = function(){
    this.name = "yjc";
    this.age = 22;
}
var child = {};
console.log(child);//Object {} ,空对象
Parent.call(child);
console.log(child); //Object {name: "yjc", age: 22}
````
以上实现了对象的继承。

##### bind的使用
obj.bind(thisObj, arg1, arg2, ...);

把obj绑定到thisObj，这时候thisObj具备了obj的属性和方法。**与call和apply不同的是，bind绑定后不会立即执行**。

同样是add()和sub()：

add.bind(sub, 5, 3); //不再返回8

add.bind(sub, 5, 3)(); //8

如果bind的第一个参数是null或者undefined，等于将this绑定到全局对象。

&nbsp;
