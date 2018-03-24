---
title: JS经典面试题
tags: 面试题
categories: 
- 前端
- JavaScript
---

1. ul中有5个li，点击打印对应的索引:
~~~ html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <ul>
        <li>1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
        <li>5</li>
    </ul>
    <script>
        // ...
    </script>
</body>
</html>
~~~

~~~ js
// this获取标签属性（不推荐）
var lis = document.querySelectorAll('li');
for (var i = 0; i < lis.length; i++) {
    lis[i].index = i;
    lis[i].onclick = function () {
        console.log(this.index);
    }
}

// 闭包
var lis = document.querySelectorAll('li');
for (var i = 0; i < lis.length; i++) {
    lis[i].onclick = (function (i) {
        return function () {
            console.log(i);
        }
    }(i))
}

// es6
var lis = document.querySelectorAll('li');
for (let i = 0; i < lis.length; i++) {
    lis[i].onclick = function () {
        console.log(i);
    }
}
~~~

2. 每隔1s依次打印从1到10：
~~~ js
window.onload = function () {
    for (var i = 0; i < 10; i++) {
        setTimeout((function (i) {
            return function () {
                console.log(i + 1);
            }
        }(i)), 1000 * i);
    }
}
~~~

