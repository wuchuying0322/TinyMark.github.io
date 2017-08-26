---
title: Ajax
tags: Ajax
categories: 面试题
---

1. 什么是Ajax？（异步/同步）

		Asynchronous JavaScript And XML
		Ajax是javascript、XML、CSS、Dom等多个技术的组合，它不是一门新技术。
		Ajax技术实现了一个静态页面在不刷新整个页面的情况下与服务器进行通信，减少了用 户的等待时间，同时降低了网络流量，增加了用户体验的友好程度。
		
		Ajax的核心技术是XMLHttpRequest，它是一个对象。

2. 实现Ajax请求：
		
		原生：
		get请求：
		var xhr = new XMLHttpRequest();
		xhr.open('get','serverUrl');
		xhr.send(null);
		xhr.onreadystatechange = function (){
			if( xhr.readyState == 4 && xhr.status == 200 ){
				var result = xhr.responseText;
				//do something...
			}
		}

		post请求：
		var xhr = new XMLHttpRequest();
		xhr.open('post','serverUrl');
		xhr.setRequestHeader('Content-Type','application/x-www-form-urlencoded'); 
		xhr.send('foo=abc&&bar=123');
		xhr.onreadystatechange = function (){
			if( xhr.readyState == 4 && xhr.status == 200 ){
				var result = xhr.responseText;
				//do something...
			}
		}

		200代表成功、304文档未修改、403没有权限、404未找到、500服务器错误