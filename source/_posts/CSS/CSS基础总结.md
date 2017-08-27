---
title: CSS基础总结
tags: CSS
categories: CSS
---

* CSS选择器有哪些？
	1. id选择器		(#myid)
	2. 类选择器		(.myclassname)
	3. 标签选择器		(div,h1,p)
	4. 相邻选择器		(h1 + p)
	5. 子代选择器		(ul > li)
	6. 后代选择器		(li a)
	7. 通配符选择器	(*)
	8. 属性选择器		(a[rel = "ex"])
	9. 伪类选择器		(a:hover,li:nth-child)
	
* 可继承的样式：
	* font-size,font-family,color,ul,li,dl,dd,dt;
* 不可继承的样式：
	* border,padding,margin,width,height;
	
* CSS 优先级的选择过程？
	* 优先级复合就近原则，同权重的情况下有限选择最近的属性。
	* 载入样式的话是以最后载入的定位为准。
	* 优先级：!important > id > class > tag（important要优先于内联样式）

* 如何居中 div？如何居中一个浮动元素？如何让绝对定位的div居中？

	**div居中：**

		给div一个宽度，然后添加"margin: 0 auto;"属性即可。

	**浮动元素居中：**

		确定容器的宽高：w500，h300 的层
		设置层的外边距；
		.div{
			width: 500px;
			height: 300px;			
			margin: -150px 0 0 -250px;
			position: relative;
			background-color: pink;
			left: 50%;
			top: 50%;
		}

	**绝对定位的div居中：**

		.div{
			position: absolute;
			width: 1200px;
			background: none;
			margin: 0 auto;
			top: 0;
			right: 0;
			bottom: 0;
			left: 0;			
		}

* 属性display 有哪些值？说明他们的作用。

		block			像块级元素一样显示
		none			默认值，像行内元素一样显示
		inline-block	像行内元素一样显示，但其内容像块级元素一样显示
		list-item		像块级元素一样显示，并添加样式列表的标记
		table			此元素会作为块级表格来显示
		inherit			规定应该从父元素继承display属性的值


	