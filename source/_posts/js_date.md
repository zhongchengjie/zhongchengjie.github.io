---
title: javasript日期操作
date: 2018-05-10 22:29:19
tags:
  - date
  - javascript
categories: javascript
---

##### 基本方法
+ var myDate = new Date();//获取日期对象
+ myDate.getFullYear(); //获取完整的年份(4位,1970-????)
+ myDate.getMonth(); //获取当前月份(0-11,0代表1月)
+ myDate.getDate(); //获取当前日(1-31)
+ myDate.getDay(); //获取当前星期X(0-6,0代表星期天)
+ myDate.getTime(); //获取当前时间(从1970.1.1开始的毫秒数)
+ myDate.getHours(); //获取当前小时数(0-23)
+ myDate.getMinutes(); //获取当前分钟数(0-59)
+ myDate.getSeconds(); //获取当前秒数(0-59)
+ myDate.getMilliseconds(); //获取当前毫秒数(0-999)
+ myDate.toLocaleDateString(); //获取当前日期(字符串格式，如：2017/11/16)
+ myDate.toLocaleTimeString(); //获取当前时间(字符串格式，如：下午4:59:16)
+ myDate.toLocaleString( ); //获取日期与时间(字符串格式，如：2017/11/16 下午4:59:45)

##### 日期格式化
```javascript
//格式化方法
Date.prototype.format = function(format)
{
    var o = {
        "M+": this.getMonth() + 1, //month
        "d+": this.getDate(),    //day
        "H+": this.getHours(),   //hour
        "m+": this.getMinutes(), //minute
        "s+": this.getSeconds(), //second
        "q+": Math.floor((this.getMonth() + 3) / 3),  //quarter
        "S": this.getMilliseconds() //millisecond
    }
    if (/(y+)/.test(format)) format = format.replace(RegExp.$1,
    (this.getFullYear() + "").substr(4 - RegExp.$1.length));
    for (var k in o)
      if (new RegExp("(" + k + ")").test(format))
        format = format.replace(RegExp.$1,
        RegExp.$1.length == 1 ? o[k] :
       ("00" + o[k]).substr(("" + o[k]).length));
    return format;
};
//使用
var d = new Date();
var f = d.format("yyyy-MM-dd"); //或d.format("yyyy-MM-dd HH:mm:ss");
console.log(f);
```

##### 日期时间字符串转Date对象
````javascript
var dateStr = '2015-03-30';    //或var dateStr = '2015-03-30 12:12:09'
dateStr = dateStr.replace(/-/g,'/');
var d = new Date(dateStr);
console.log(d);        //输出 Mon Mar 30 2015 00:00:00 GMT+0800 (中国标准时间)
````
##### 获取某月的天数
```javascript
//year传入年份，如：2015；month传入月份，范围：1-12
function getDaysInMonth(year,month){
    var dayCount;
    now = new Date(year,month, 0);
    dayCount = now.getDate();
    return dayCount;
}
```
