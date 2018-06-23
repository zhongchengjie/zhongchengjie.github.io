---
title: gulp入门
date: 2018-06-21 11:33:58
tags:
 - gulp
---


参考文章：[http://www.ydcss.com/archives/18—gulp详细入门教程][link1]

[link1]:http://www.ydcss.com/archives/18 "gulp详细入门教程"

#### 简介
gulp是基于Nodejs的自动任务运行器， 她能自动化地完成 javascript/coffee/sass/less/html/image/css 等文件的的测试、检查、合并、压缩、格式化、浏览器自动刷新、部署文件生成，并监听文件在改动后重复指定的这些步骤。在实现上，她借鉴了Unix操作系统的管道（pipe）思想，前一级的输出，直接变成后一级的输入，使得在操作上非常简单。

#### 使用

##### 1. 安装nodejs
gulp是基于nodejs，使用gulp前需要先安装nodejs。[https://nodejs.org/en/—nodejs官网][link2]。

[link2]:https://nodejs.org/en/ "nodejs"

##### 2. 全局安装gulp
安装好nodejs是，npm会随之一起安装。打开命令行窗口，执行如下命令：
``` javascript
npm install gulp -g
```
检查gulp是否安装成功，用如下命令：
``` javascript
gulp -v
```

##### 3. 新建package.json文件
package.json是基于nodejs项目必不可少的配置文件，它是存放在项目根目录的普通json文件。
在项目根目录下执行如下命令来新建package.json。
``` javascript
npm init
```
注意：**package.json是一个普通json文件，所以不能添加任何注释。**

##### 项目安装gulp及gulp插件
在项目中安装glup：
``` javascript
npm install gulp --save-dev
```
在项目中安装gulp插件，这里以gulp-less（编译less文件）为例：
``` javascript
npm install gulp-less --save-dev
```
注意：**全局安装gulp是为了执行gulp任务，本地安装gulp则是为了调用gulp插件的功能。**

##### 配置gulpfile.js
gulpfile.js是gulp项目的配置文件，是位于项目根目录的普通js文件。gulpfile.js大概是这样一个js文件：
``` javascript
//导入工具包 require('node_modules里对应模块')
var gulp = require('gulp'), //本地安装gulp所用到的地方
    less = require('gulp-less');

//定义一个testLess任务（自定义任务名称）
gulp.task('testLess', function () {
    gulp.src('src/less/index.less') //该任务针对的文件
        .pipe(less()) //该任务调用的模块
        .pipe(gulp.dest('src/css')); //将会在src/css下生成index.css
});

gulp.task('default',['testLess', 'elseTask']); //定义默认任务 elseTask为其他任务，该示例没有定义elseTask任务

//gulp.task(name[, deps], fn) 定义任务  name：任务名称 deps：依赖任务名称 fn：回调函数
//gulp.src(globs[, options]) 执行任务处理的文件  globs：处理的文件路径(字符串或者字符串数组)
//gulp.dest(path[, options]) 处理完后文件生成路径
```

##### 运行任务
在项目根目录下执行如下命令：
``` javascript
gulp default
```

&nbsp;
