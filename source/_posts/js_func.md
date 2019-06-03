---
title: javasript函数
date: 2018-06-02 20:21:19
tags:
  - 函数
  - javascript
categories: javascript
---

#### 函数参数
1. arguments只在函数内部起作用，并且永远指向当前函数的调用者传入的所有参数。arguments类似 Array但它不是一个Array。arguments最常用于判断传入参数的个数。
2. ES6标准引入了rest参数，用于获取额外的参数。rest参数只能写在最后，前面用...标识。
```
function foo(a, b, ...rest) {
    console.log('a = ' + a);
    console.log('b = ' + b);
    console.log(rest);
}
foo(1, 2, 3, 4, 5);
// 结果:
// a = 1
// b = 2
// Array [ 3, 4, 5 ]
foo(1)
// 结果:
// a = 1
// b =undefined
// Array []
```

#### 全局作用域
不在任何函数内定义的变量就具有全局作用域。实际上，JavaScript默认有一个全局对象window，全局作用域的变量实际上被绑定到window的一个属性。顶层函数同理。

#### 局部作用域
1. 由于JavaScript的变量作用域实际上是函数内部，在for循环等语句块中是无法定义具有局部作用域的变量。
```
function foo() {
    for (var i=0; i<100; i++) {
        //
    }
    i += 100; // 仍然可以引用变量i
}
```
2. 为了解决块级作用域，ES6引入了新的关键字let，用let替代var可以申明一个块级作用域的变量。
```
function foo() {
    for (let i=0; i<100; i++) {
        //
    }
    // SyntaxError:
    i += 1;
}
```

#### 解构赋值
1. 数组解构赋值
```
let [x, [y, z]] = ['hello', ['JavaScript', 'ES6']];
x; // 'hello'
y; // 'JavaScript'
z; // 'ES6'
```
2. 对象解构赋值
```
var person = {
    name: '小明',
    age: 20,
    gender: 'male',
    passport: 'G-12345678',
    school: 'No.4 middle school',
    address: {
        city: 'Beijing',
        street: 'No.1 Road',
        zipcode: '100001'
    }
};
var {name, address: {city, zip}} = person;
name; // '小明'
city; // 'Beijing'
zip; // undefined, 因为属性名是zipcode而不是zip
// 注意: address不是变量，而是为了让city和zip获得嵌套的address对象的属性:
address; // Uncaught ReferenceError: address is not defined
```

#### 方法
1. 在一个对象中绑定函数，称为这个对象的方法。
2. 在一个方法内部，this是一个特殊变量，它始终指向当前对象。
```
var xiaoming = {
    name: '小明',
    birth: 1990,
    age: function () {
        var y = new Date().getFullYear();
        return y - this.birth;
    }
};
xiaoming.age();
```
3. 以对象的方法形式调用，该函数的this指向被调用的对象。如果单独调用函数，该函数的this指向全局对象，也就是window。
```
function getAge() {
    var y = new Date().getFullYear();
    return y - this.birth;
}
var xiaoming = {
    name: '小明',
    birth: 1990,
    age: getAge
};
xiaoming.age(); // 28, 正常结果
getAge(); // NaN
```
4. 用函数本身的apply方法，可以改变this的指向。它接收两个参数，第一个参数就是需要绑定的this变量，第二个参数是Array，表示函数本身的参数。
```
function getAge() {
    var y = new Date().getFullYear();
    return y - this.birth;
}
var xiaoming = {
    name: '小明',
    birth: 1990,
    age: getAge
};
getAge.apply(xiaoming, []); // 25, this指向xiaoming, 参数为空
```
#### 高阶函数
 一个函数就可以接收另一个函数作为参数，这种函数就称之为高阶函数。
1. map/reduce
   ......
2. filter
   ......
3. sort
   通常规定，对于两个元素x和y，如果认为x < y，则返回-1，如果认为x == y，则返回0，如果认为x > y，则返回1。 Array的sort()方法默认把所有元素先转换为String再排序，结果'10'排在了'2'的前面，因为字符'1'比字符'2'的ASCII码小。

#### 箭头函数
箭头函数相当于匿名函数，并且简化了函数定义。
箭头函数看上去是匿名函数的一种简写，但实际上，箭头函数和匿名函数有个明显的区别：箭头函数内部的this是词法作用域，由上下文确定。
```
var obj = {
    birth: 1990,
    getAge: function () {
        var b = this.birth; // 1990
        var fn = () => new Date().getFullYear() - this.birth; // this指向obj对象
        return fn();
    }
};
obj.getAge(); // 25
```
