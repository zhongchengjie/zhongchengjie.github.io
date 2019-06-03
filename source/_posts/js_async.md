---
title: javasript异步
date: 2018-06-01 20:29:19
tags:
  - 异步
  - javascript
categories: javascript
---

####  JavaScript异步
+ JS 是单线程的语言
+ 在浏览器端运行的 js ，可能会有大量的网络请求，而一个网络资源啥时候返回，这个时间是不可预估的。
+ 函数传递过去不会立即执行，而是等着请求成功之后才能执行。对于这种传递过去不执行，等出来结果之后再执行的函数，叫做callback，即回调函数
+ 实现异步的最核心原理，就是将callback作为参数传递给异步执行函数，当有结果返回之后再触发 callback执行
+ 常见的异步操作：网络请求，如ajax http.get；IO 操作，如readFile readdir；定时函数，如setTimeout setInterval
+ 异步操作是系统自动调用，无论是setTimeout时间到了还是$.ajax请求返回了，系统会自动调用。而事件绑定就需要用户手动触发。
+ 1.5 版本之后的$.ajax()返回一个deferred对象，这个对象就带有done和fail的方法，并且是等着请求返回之后再去调用。
```javascript
var ajax = $.ajax('data.json')
ajax.done(function () {
        console.log('success 1')
    })
    .fail(function () {
        console.log('error')
    })
    .done(function () {
         console.log('success 2')
    })

console.log(ajax) // 返回一个 deferred 对象
```
+ promise对象相比于deferred对象，缺少了.resolve和.reject这俩函数属性。返回promise的好处：（1）函数内部，使用dtd.resolve()来改状态，做主动的修改操作；（2）waitHandle最终返回promise对象，只能去被动监听变化（then函数），而不能去主动修改操作。
