---
title: css box-sizing
date: 2018-06-25 20:18:59
tags:
  - box-sizing
  - 盒子模型
  - css/css3
categories: html/css
---
##### css盒子模型
标准盒子模型：宽度=内容的宽度（content）+ border + padding + margin
低版本IE盒子模型：宽度=内容宽度（content+border+padding）+ margin

##### box-sizing与盒子模型
用来控制元素的盒子模型的解析模式，默认为content-box。
context-box：W3C的标准盒子模型，设置元素的 height/width 属性指的是content部分的高/宽。
border-box：IE传统盒子模型。设置元素的height/width属性指的是border + padding + content部分的高/宽。
```
 <!DOCTYPE html>
 <html>
 	<head>
 		<meta charset="UTF-8">
 		<title></title>
 		<style>
 		   .div1{border:1px solid #ccc;padding:10px;box-sizing:content-box;width:200px;}
 		   .div2{margin-top:10px;border:1px solid #ccc;padding:10px;box-sizing:border-box;width:200px;}
 		   .div3{margin-top:10px;border:1px solid #ccc;padding:10px;width:200px}
 		</style>
 	</head>
 	<body>

 		<div class="div1" id="div1">box-sizing:content-box</div>
 		<div class="div2" id="div2">box-sizing:border-box</div>
 		<div class="div3" id="div3">default</div>
 		<script src="skin/jquery/jquery-1.12.4.js"></script>
 		<script>
 			var height1 = $("#div1").css("height");
 			var height2 = $("#div2").css("height");
                         var width1 = $("#div1").css("width");
                         var width2 = $("#div2").css("width");
 			console.log(width1+" "+height1);       //输出：200px 21px  这里的高宽即为content部分的高/宽
 			console.log(width2+" "+height2);       //输出：200px 43px  这里的高宽即为border + padding + content部分的高/宽
 		</script>
 	</body>
 </html>
```