---
title: css水平居中
date: 2018-06-21 20:12:59
tags:
  - 布局
  - 水平居中
  - html/css
categories: html/css
---
#### 宽度不确定水平居中的多种实现方式

##### 方式1：text-align:center+display:inline-block
```
<div style="background:#ddd;text-align: center;">
    <div style="background:#666;color:#fff;display: inline-block;">Hello World</div>
</div>
```

##### 方式2：margin:0 auto+display:table
```
<div style="background:#ddd;">
    <div style="background:#666;color:#fff;margin:0px auto;display: table">Hello World</div>
</div>
```

##### 方式3：position:absolute+transform:translateX()
```
<div style="background:#ddd;position:relative">
    <div style="background:#666;color:#fff;position:absolute;right:50%;transform: translateX(50%);">Hello World</div>
</div>
```

##### 方式4：display:flex+justify-content: center
```
<div style="background:#ddd;display: flex;justify-content: center;">
    <div style="background:#666;color:#fff">Hello World</div>
</div>
```