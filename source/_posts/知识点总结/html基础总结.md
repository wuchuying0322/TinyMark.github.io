---
title: html基础总结
tags: html
categories: 
- FrontEnd
- HTML
---

# 1. 行内元素和块级元素的区别？行内块元素的兼容性使用？（IE8 以下）                                           ~~~    
行内元素：会在水平方向排列，不能包含块级元素，设置width无效，height无效(可以设置line-height)，margi下无效，padding上下无效。

块级元素：各占据一行，垂直方向排列。从新行开始结束接着一个断行。

兼容性：display:inline-block;*display:inline;*zoom:1;
~~~
<!-- more --> 

响应式布局会改变排版的样式
自适应只是等比例缩放，不改变排版样式

块元素不设置高度，默认继承父元素的高度


