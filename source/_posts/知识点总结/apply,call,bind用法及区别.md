---
title: apply,call,bind 的用法及区别
tags: JS
date: 2017/7/12
categories: 
- FrontEnd
- JavaScript
---

# apply
~~~js
func.apply(tag, [arg1, arg2])
// 改变this，立即执行，参数使用数组传入
~~~

<!-- more --> 

# call
~~~js
func.call(tag, arg1, arg2)
// 改变this，立即执行，参数依次传入
~~~
# bind
~~~js	
func.bind(tag, arg1, arg2)
// 改变this，不立即执行，参数依次传入
~~~