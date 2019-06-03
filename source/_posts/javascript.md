---
title: javascript知识整理-基础项
date: 2018-04-22 00:11:50
tags:
 - javascript
categories: javascript
---

#### 简介
JavaScript是一种运行在浏览器中的解释型的编程语言，能够跨平台、跨浏览器驱动网页，与用户交互。

#### JavaScript与ECMAScript
ECMAScript是一种语言标准，而JavaScript是网景公司对ECMAScript标准的一种实现。

#### 数据类型
在JavaScript中定义了以下几种数据类型：字符串、数字、 布尔、 数组、 对象、Null和Undefined。
1. 字符串
   1.1 JavaScript的字符串就是用''或""括起来的字符表示。
   1.2 ES6标准新增了一种多行字符串的表示方法，用反引号 ` ... ` 表示：
   1.3 ES6新增了一种模板字符串，用${变量名}表示。放在多行字符串中才会生效。
2. 数字
   2.1 console.log(2/0)     // Infinity 表示无限大
   2.2 console.log(0/0)     // NaN 表示无法计算结果
  2.3 Infinity和NaN都是Number类型
3. 布尔
   3.1 JavaScript把null、undefined、0、NaN和空字符串''视为false，其他值一概视为true。
4. 数组
    4.1 js的Array可以包含任意数据类型。 例如：[1, 2, 3.14, 'Hello', null, true];
    4.2 直接给Array的length赋一个新的值会导致Array大小的变化。
    4.3 对Array的索引进行赋值会直接修改这个Array。
    4.4 js的Array允许越界访问。
5. 对象
    5.1 对象的属性名必须是一个有效的变量名。如果属性名包含特殊字符，就必须用''括起来。
          var xiaohong = {
          name: '小红',
          'middle-school': 'No.1 Middle School'
       };
   5.2 判断一个属性是否是对象自身拥有的，而不是继承得到的，可以用hasOwnProperty()。
  var xiaoming = {
      name: '小明'
  };
  xiaoming.hasOwnProperty('name'); // true
  xiaoming.hasOwnProperty('toString'); // false
6. Map
    6.1 Map是一组键值对的结构，具有极快的查找速度。
    6.2 对象的键必须是字符串，而Map的键可以为其它类型。
    6.3 使用new Map()定义。
  var m = new Map([['Michael', 95], ['Bob', 75], ['Tracy', 85]]);
  m.get('Michael'); // 95
  m.get('pecy');  //undefined
7. iterable
   7.1 遍历Array可以采用下标循环，遍历Map和Set就无法使用下标。为了统一集合类型，ES6标准引入了新的iterable类型，Array、Map和Set都属于iterable类型。
    7.2 具有iterable类型的集合可以通过新的for ... of循环来遍历。
          var a = ['A', 'B', 'C'];
       var s = new Set(['A', 'B', 'C']);
       var m = new Map([[1, 'x'], [2, 'y'], [3, 'z']]);
       for (var x of a) { // 遍历Array
          console.log(x);
       }
       for (var x of s) { // 遍历Set
          console.log(x);
       }
       for (var x of m) { // 遍历Map
          console.log(x[0] + '=' + x[1]);
       }

#### 比较运算符“==”与“===”
1. “==”比较，它会自动转换数据类型再比较； “===”比较，它不会自动转换数据类型，如果数据类型     不一致，返回false，如果一致，再比较。
2. 另一个例外是NaN这个特殊的Number与所有其他值都不相等，包括它自己。唯一能判断NaN的方  法是通过isNaN()函数。
    false == 0;            // true
    false === 0;          // false
    NaN === NaN;     // false
    isNaN(NaN);        // true

#### 变量
1. 变量在JavaScript中就是用一个变量名表示，变量名是大小写英文、数字、$和_的组合，且不能用数字开头。变量名也不能是JavaScript的关键字，如if、while等。申明一个变量用var。
2. 变量本身类型不固定的语言称之为动态语言，与之对应的是静态语言。

#### null与undefined
null表示一个空的值，而undefined表示值未定义。事实证明，这并没有什么卵用，区分两者的意义不大。大多数情况下，我们都应该用null。undefined仅仅在判断函数参数是否传递的情况下有用。