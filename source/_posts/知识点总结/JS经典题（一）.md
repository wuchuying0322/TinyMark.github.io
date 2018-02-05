---
title: JS经典题（一）
tags: JS
categories: 
- FrontEnd
- JavaScript
---

1. 点击列表中的 li 标签，输出对应索引：

		var lis = document.querySelectorAll('li');
		//常规做法：
		for (var i = 0; i < lis.length; i++) {
			lis[i].index = i;
	        lis[i].addEventListener('click',function(){
	            console.log(this.index)
	        })
	    }

		// es6语法：
        for (let i = 0;i < lis.length;i++){
            lis[i].addEventListener('click',function(){
                console.log(i);
            })
        };

		// 闭包做法：
        for (var i = 0; i < lis.length; i++) {
            (function (n) {
                lis[i].addEventListener('click', function () {
                    console.log(n);
                })
            })(i)
        }
