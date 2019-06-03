---
title: 用css画三角形
date: 2018-01-22 00:18:59
tags:
  - css三角形
  - html/css3
categories: html/css
---
#### 原理
最原始的三角形：设置元素的高度和宽度为0，并结合border属性。

##### 1. 向上的三角形
```
  .triangle_up {
     height:0;
     width:0;
     border-width:10px;
     border-style:solid;
     border-color: transparent transparent #000
  }
```
##### 2. 向下的三角形
```
  .triangle_up {
     height:0;
     width:0;
     border-width:10px;
     border-style:solid;
     border-color: #000 transparent transparent
  }
```

##### 3. 向左的三角形
```
  .triangle_up {
     height:0;
     width:0;
     border-width:10px;
     border-style:solid;
     border-color: transparent #000 transparent transparent
  }
```

##### 4. 向又的三角形
```
  .triangle_up {
     height:0;
     width:0;
     border-width:10px;
     border-style:solid;
     border-color: transparent transparent transparent #000
  }
```