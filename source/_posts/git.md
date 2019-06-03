---
title: git常用操作
date: 2018-03-26 21:14:07
tags:
  - git
  - git常用命令行
categories: 工具
---

#### 简介
Git是目前世界上最先进的分布式版本控制系统。

#### 安装git
从git官网中下载安装程序，然后按默认选项安装即可。

#### 常用命令
1.&nbsp;clone远程库项目到本地
```
 git clone https://......
 //例如
 git clone https://github.com/zhongchengjie/my-demo.git
```

2.&nbsp;同步远程库项目到本地
```
 git pull origin master(分支用对应的分支名称代替master)
```

3.&nbsp;将本地的新项目上传到远程库
```
 git init
 git add .
 git commit -m "提交的备注信息"
 git remote add origin https://......
 git push -u origin master
```

4.&nbsp;提交本地库的更新到远程库
```
git add .
git commit -a -m "提交的备注信息"
git push origin master(分支用对应的分支名称代替master)
```

5.&nbsp;本地库创建分支并push到远程库
```
git branch branch1   （创建新分支，branch1是分支名称）
git checkout branch1 （切换到分支）
git push origin branch1（push到远程库）
```

6.&nbsp;强制更新远程库来覆盖本地库
```
git fetch --all
git reset --hard origin/master (分支用对应的分支名称代替master)
```

7.&nbsp;拉取远程库分支代码到本地
```
git checkout origin/remoteName -b localName
```