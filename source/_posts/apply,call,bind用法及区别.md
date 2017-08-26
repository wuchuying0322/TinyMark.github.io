---
title: apply,call,bind的用法及区别
tags: JS
categories: 知识点总结
---

* **apply**

	func.call(tag, [arg1, arg2])
	改变this，立即执行，参数使用**数组**传入
* **call** 

	func.apply(tag, arg1, arg2)
	改变this，立即执行，**参数依次传入**
* **bind** 
	
	func.bind(tag, arg1, arg2)
    改变this，**不立即执行**，参数依次传入