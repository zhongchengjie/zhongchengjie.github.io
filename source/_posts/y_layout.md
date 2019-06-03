---
title: css垂直居中
date: 2018-06-21 20:33:59
tags:
  - 布局
  - 垂直居中
  - html/css
categories: html/css
---
#### 垂直居中的多种实现方式

##### 方式1：vertical-align:middle+display:table-cell
```
<div style="background:#ddd;height:200px;width:100px;vertical-align: middle;display: table-cell">
    <div style="background:#666;color:#fff;width:100%">Hello World</div>
</div>
```

##### 方式2：display:flex+align-items:center
```
<div style="background:#ddd;height:200px;width:100px;display: flex;align-items: center">
    <div style="background:#666;color:#fff;width:100%">Hello World</div>
</div>
```

##### 方式3：position:absolute+transform: translateY(-50%);
```
<div style="background:#ddd;height:200px;width:100px;position: relative;">
    <div style="background:#666;color:#fff;width:100%;position:absolute;top:50%;transform: translateY(-50%);">Hello World</div>
</div>
```