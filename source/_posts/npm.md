---
title: npm介绍
date: 2018-06-21 10:53:45
tags:
  - npm
  - cnpm
  - nodejs
categories: nodejs
---

#### npm简介
npm（node package manager）nodejs的包管理器，用于node插件管理（包括安装、卸载、管理依赖等）。

#### npm常用命令
1.安装插件：**npm install <name> [-g] [--save-dev]**
+ <name>：node插件名称。例：npm install gulp-less --save-dev
+ -g：全局安装。将会安装在C:\Users\Administrator\AppData\Roaming\npm，并且写入系统环境变量；  非全局安装：将会安装在当前定位目录；  全局安装可以通过命令行在任何地方调用它，本地安装将安装在定位目录的node_modules文件夹下，通过require()调用。
+ --save：将保存配置信息至package.json（package.json是nodejs项目配置文件）
+ -dev：保存至package.json的devDependencies（开发环境）节点，不指定-dev将保存至dependencies（生产环境）节点。

  为什么要保存至package.json？**因为node插件包相对来说非常庞大，所以不加入版本管理，将配置信息写入package.json并将其加入版本管理，其他开发者对应下载即可（命令提示符执行npm install，则会根据package.json下载所有需要的包，npm install --production只下载dependencies节点的包）**

2.卸载插件：**npm uninstall <name> [-g] [--save-dev]**

3.卸载全部插件：先安装rimraf：**npm install rimraf -g** &nbsp;&nbsp;用法：**rimraf node_modules**

4.更新插件：**npm update <name> [-g] [--save-dev]**

5.更新全部插件：**npm update [--save-dev]**

6.查看已安装的插件：**npm list**

**devDependencies节点下的模块是我们在开发时需要用的，比如项目中使用的gulp，压缩css、js的模块。这些模块在我们的项目部署后是不需要的，所以我们可以使用 -save-dev 的形式安装。像 express 这些模块是项目运行必备的，应该安装在 dependencies 节点下，所以我们应该使用 -save 的形式安装。**


#### cnpm简介
因为npm安装插件是从国外服务器下载，受网络影响大，可能出现异常。**cnpm是一个完整npmjs.org镜像，你可以用此代替官方版本(只读)，同步频率目前为 10分钟 一次以保证尽量与官方服务同步。**
#### cnpm安装
安装命令：**npm install cnpm -g --registry=https://registry.npm.taobao.org**

检查是否安装成功：**cnpm -v**
