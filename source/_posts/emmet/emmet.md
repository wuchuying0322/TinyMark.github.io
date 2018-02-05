---
title: emmet语法简介
tags: emmet
categories: 
- 杂
---

Emmet是一个能大幅度提高前端开发效率的一个工具，目前市面上主流编辑器中都有集成（如 vscode,webstrom 等）。

使用Emmet插件可以方便大家快速书写代码来编写页面结构。

语法如下，写完后用Tab补全即可：

后代：>
* nav>ul>li
~~~ javascript
    <nav>
        <ul>
            <li></li>
        </ul>
    </nav>
~~~


兄弟：+
* div+p+span
~~~ javascript
    <div></div>
    <p></p>
    <span></span>
~~~


乘法：*
* ul>li*5
~~~ javascript
    <ul>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
    </ul>
~~~


分组：( )
* div>(header>ul>li*2>a)+footer>p
~~~ javascript
    <div>
        <header>
            <ul>
                <li><a href=""></a></li>
                <li><a href=""></a></li>
            </ul>
        </header>
        <footer>
            <p></p>
        </footer>
    </div>
~~~

自增符号：$
1. ul>li.item$*5
~~~ javascript
    <ul>
        <li class="item1"></li>
        <li class="item2"></li>
        <li class="item3"></li>
        <li class="item4"></li>
        <li class="item5"></li>
    </ul>
~~~
2. ul>li.item$$$*5
~~~ javascript
    <ul>
        <li class="item001"></li>
        <li class="item002"></li>
        <li class="item003"></li>
        <li class="item004"></li>
        <li class="item005"></li>
    </ul>
~~~
3. ul>li.item$@-*5
~~~ javascript
    <ul>
        <li class="item1@-"></li>
        <li class="item2@-"></li>
        <li class="item3@-"></li>
        <li class="item4@-"></li>
        <li class="item5@-"></li>
    </ul>
~~~
4. ul>li.item$@3*5
~~~ javascript
    <ul>
        <li class="item3"></li>
        <li class="item4"></li>
        <li class="item5"></li>
        <li class="item6"></li>
        <li class="item7"></li>
    </ul>
~~~

ID: #
* #header
~~~ javascript
    <div id="header"></div>
~~~

类: .
1. .title
~~~ javascript
    <div class="title"></div>
~~~
2. form#search.wide
~~~ javascript
    <form action="" id="search" class="wide"></form>
~~~

属性：[]
* p[title="Hello world"]
~~~ javascript
    <p title="Hello world"></p>
~~~

文本：{}
* a{Click me}
~~~ javascript
    <a href="">Click me</a>
~~~