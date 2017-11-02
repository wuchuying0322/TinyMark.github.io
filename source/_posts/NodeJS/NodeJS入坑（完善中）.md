---
title: TypeScript 不完全指北
tags: 框架
categories: Angular
---

# NodeJS 简介

## 官方定义
* Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境。 
* Node.js 使用了一个事件驱动、非阻塞式 I/O 的模型，使其轻量又高效。 
* Node.js 的包管理器 npm，是全球最大的开源库生态系统。
> 详见 [NodeJS中文网](http://nodejs.cn/)

## [下载 ](http://nodejs.cn/download/) 与 安装
* 注意 区分 32位 与 64位 系统
* 注意 大版本号，奇数激进版，偶数稳定版。建议选择 稳定版

## [3m安装法](http://cnodejs.org/topic/57f628098489e7ca69f4e839)
* npm 
> node package manager -----    node包管理
* nrm
> node registry manager -----   node仓库管理
* nvm 
> node version manager  -----   node版本管理

<p style="display:inline;font-size:18px;background-color:#353535;color:#353535">有兴趣自行百度吧，我懒得写了=。=|</p>

## 学习资源

+ 《Node.js 权威指南》：官方API详解：[https://nodejs.org/dist/latest-v6.x/docs/api/](https://nodejs.org/dist/latest-v6.x/docs/api/)
+ JavaScript 标准参考教程（alpha）: http://javascript.ruanyifeng.com/
+ Node 入门：http://www.nodebeginner.org/index-zh-cn.html
+ 中文文档（版本比较旧，凑合看）：[http://www.nodeclass.com/api/node.html](http://www.nodeclass.com/api/node.html)
+ CNODE社区：[http://cnodejs.org](http://cnodejs.org)
+ CNODE-新手入门：[http://cnodejs.org/getstart](http://cnodejs.org/getstart)
+ Node.js包教不包会：https://github.com/alsotang/node-lessons
+ 朴灵：《深入浅出Node.js》

# 基本模块

## fs
> 读写文件模块
~~~ js
var fs = require("fs");

fs.readFile("./readFile.js",function(err,data){
    if (err) {
        console.log("读取出错");
    }
    else {
        console.log(data);
    }
});

fs.writeFile("./writeFile.js","这是我自己写的内容",function(err,data){
    if (err) {
        console.log("写入文件失败");
    } else {
        console.log("写入完成");
    }
});
~~~

## http
> 服务器模块
~~~ js
var http = require('http');

var server = http.createServer(function(req, res) {
    res.write('<h1>hello word</h1>');
    res.end();
}).listen( 8888, function() {
    console.log('服务器启动成功');
});
~~~

## 