---
title: this的四种调用模式
tags: JS
categories: 知识点总结
---

# 1. 函数直接调用模式 
~~~ javascript
var foo = function(){
    console.log(this)
};
// 如果一个函数，是直接调用，与任何对象都没有关系时，这个调用，就是函数调用
// 函数调用模式中：this指的就是window
foo();
~~~

<!-- more --> 

# 2. 对象内部-方法调用模式 
~~~ javascript
var obj = {
    foo:function(){console.log(this)}
}
// 如果一个函数，是作为某个对象一个方法调用的(与某象相关联)，那么这种调用，就属于方法调用
// 方法调用模式中：this就指向了当前调用的对象
obj.foo();
~~~ 
# 3. 构造函数调用模式 
~~~ javascript
var Person = function(){
    this.foo = function(){
         console.log(this);
     }
};
// 如果一个函数是配合new运算符，来使用的，那么该种就属于，构造函数调用
// 构造函数调用模式中：this指向new创建出来的新对象
var p = new Person();
p.foo();
~~~ 
# 4. 上下文调用模式，也称借用方法 
~~~ js
call/apply/bind 可以动态改变this的指向
// 上下文调用模式中：this指向第一个参数，如果为空指向window
~~~ 
# 5. 总结this的问题 
~~~ text
不同的调用模式的区别：this的指向的对象不同
要分析函数内部this的问题：
只要记住，谁调用了函数或者方法，函数内部的this就指向了谁
也就是说要分this的问题，
不但要看函数是被怎么调用的，
还要知道当前this是属于哪个函数的
~~~ 
# * 附赠 阮老师 的传送门：
[阮一峰的网络日志 —— Javascript的this用法](http://www.ruanyifeng.com/blog/2010/04/using_this_keyword_in_javascript.html)
