---
title: 《css知多少》知识点整理
date: 2018-01-21 17:30:17
tags:
  - css/css3
categories: css/css3
---


参考文章：[https://www.cnblogs.com/wangfupeng1988/category/652232.html—css知多少][link1]

[link1]:https://www.cnblogs.com/wangfupeng1988/category/652232.html "css知多少"

#### css基础知识
1.&nbsp;css—层叠样式表，层叠就是浏览器对多个样式来源进行叠加，浏览器会通过叠加和覆盖这两种方式来生成最终的样式值，层叠是css的核心机制。
2.&nbsp;css样式来源
- 浏览器默认样式表
- 用户样式表
- &lt;link&gt;引用的css文件
- &lt;style&gt;中编写的样式代码
- &lt;a style=""&gt;中编写的样式代码

#### display属性
1.&nbsp;display:block与display:table的区别。
block元素的宽度和父容器相同，table元素宽度根据内容而定—即table具有“包裹性”。
```html
<div style="border:1px solid #ccc;padding:5px">
    display:block;(div默认block)
</div>
<div style="border:1px solid #ccc;padding:5px;display:table">
    display:table;
</div>
```
效果如下图：
![image](http://images.cnitblog.com/blog/138012/201502/090822225585144.png)
2.&nbsp;display:table-cell
table-cell可用于多列布局，但不兼容IE6和IE7。
3.&nbsp;display:inline-block
能被父容器居中、能设置高度宽度和margin、不会像table或div那样占一整行。
4.&nbsp;display:inline
常用的inline就是文字和图片。对inline设置高度和宽度是无效的，其高度和宽度是auto的。
将inline元素转换成"块元素"：
+ 对inline元素设置float
+ 对inline元素设置position:absolute/fixed

#### 选择器
css通过选择器与html结合。常见的选择器包括标签选择器、属性选择器、伪类选择器等。
1.&nbsp;+（相邻选择器），选择紧接在一个元素后的元素，而且二者有相同的父元素。只会选择第一个相邻的匹配元素。
2.&nbsp;~（匹配选择器），选择某一个元素之后的所有同胞节点。
##### 选择器优先级
1.&nbsp;!important优先级最高，高于上面一切。* 选择器最低，低于一切。
2.&nbsp;特指度表示一个css选择器表达式的重要程度，可以通过一个公式来计算出一个数值，数越大，越重要。即，针对一个css选择器表达式，遇到一个id就往特指度数值中加100，遇到一个class就往特指度数值中加10，遇到一个element就往特指度数值中加1。
这个计算叫做“I-C-E”计算公式。
+ I——Id——100
+ C——Class——10
+ E——Element——1

#### float
1.&nbsp;float被设计出来的初衷是用于——文字环绕效果
2.&nbsp;float会破坏父标签的原本结构，使得父标签出现了坍塌现象。导致这一现象的最根本原因在于：被设置了float的元素会脱离文档流。
3.&nbsp;div设置了float之后，其宽度会自动调整为包裹住内容宽度，而不是撑满整个父容器。
4.&nbsp;清除浮动
+ 通过在所有浮动元素下方添加一个clear:both的元素，可以消除float的破坏性。
+ clearfix
```html
<style>
    .clearfix:after { content: ''; display: table; clear: both; }
    .clearfix: { zoom: 1; }
</style>
```

#### position
##### 1.&nbsp;relative
+ relative会导致自身位置的相对变化，而不会影响其他元素的位置、大小的变化。
+ relative产生一个新的定位上下文。

##### 2.&nbsp;absolute
+ absolute元素脱离文档结构，会产生破坏结构。
+ absolute元素具有“包裹性”。
+ 设置absolute会使得元素已有的float失效。不过float和absolute同时使用的情况不多。
+ absolute元素会悬浮在页面上方，会遮挡住下方的页面内容。

##### 3.&nbsp;fixed
+ fixed和absolute是一样的，唯一的区别在于：absolute元素是根据最近的定位上下文确定位置，而fixed永远根据浏览器确定位置。
