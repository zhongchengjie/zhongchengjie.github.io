---
title: js中的undefined与null
date: 2018-05-03 22:46:54
tags:
 - undefined
 - null
 - js数据类型
categories: javascript
---


参考文章：[js判断undefined类型,undefined,null, 的区别详细解析][link1]

[link1]:https://www.jb51.net/article/44472.htm

##### 类型分析
js中的数据类型有undefined,boolean,number,string,object等5种，前4种为原始类型，第5种为引用类型。
````javascript
var a1;
var a2 = true;
var a3 = 1;
var a4 = "Hello";
var a5 = new Object();
var a6 = null;
var a7 = NaN;
var a8 = undefined;
alert(typeof a);   //显示"undefined"
alert(typeof a1);  //显示"undefined"
alert(typeof a2);  //显示"boolean"
alert(typeof a3);  //显示"number"
alert(typeof a4);  //显示"string"
alert(typeof a5);  //显示"object"
alert(typeof a6);  //显示"object"
alert(typeof a7);  //显示"number"
alert(typeof a8);  //显示"undefined"
````
从上面的代码中可以看出**未定义的值和定义未赋值的为undefined**，null是一种特殊的object,NaN是一种特殊的number。

##### 比较运算
````javascript
var a1;  //a1的值为undefined
var a2 = null;
var a3 = NaN;
alert(a1 == a2);  //显示"true"
alert(a1 != a2);  //显示"false"
alert(a1 == a3);  //显示"false"
alert(a1 != a3);  //显示"true"
alert(a2 == a3);  //显示"false"
alert(a2 != a3);  //显示"true"
alert(a3 == a3);  //显示"false"
alert(a3 != a3);  //显示"true"
````
从上面的代码可以得出结论：
+ **undefined与null是相等；**
+ **NaN与任何值都不相等，与自己也不相等。**

##### undefined判断
用 === 运算或typeof来测试某个值是否是未定义的。**undefined表示一个未声明的变量，或已声明但没有赋值的变量，或一个并不存在的对象属性**。在本例中，我们将检测两个变量中未定义的一个：
````javascript
var t1=""
var t2
if (t1===undefined) {document.write("t1 is undefined")}
if (t2===undefined&&typeof(t2)=="undefined") {document.write("t2 is undefined")}

//输出：t2 is undefined
````
