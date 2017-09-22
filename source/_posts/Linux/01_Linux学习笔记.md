---
title: Linux学习笔记（一）
tags: Linux
categories: Linux
---

# 常用基础操作命令
* pwd 显示当前所在的路径
    ~~~
    // 显示当前所在路径
    $ pwd
    /c/Users/Jack/
    ~~~

* touch 创建一个文件
    > 注意加 后缀名

    ~~~
    // 创建一个名为 test.txt 的文件
    $ touch test.txt
    ~~~

* mkdir 创建一个文件夹
    ~~~
    // 创建一个名为 bash 的文件夹
    $ mkdir bash
    ~~~

* ls 显示当前路径下的文件/文件夹的信息
    ~~~
    // 显示当前路径下的文件或文件夹信息
    $ ls
    bash/   test.txt
    ~~~

* rm 删除一个文件/文件夹 ( -r )
    ~~~
    // 删除名为 test.txt 的文件
    $ rm test.txt

    // 删除名为 bash 的文件夹
    $ rm bash -r
    ~~~

* cd 跳转到某个路径
    > 相对路径：

    ~~~
    $ cd ../..
    ~~~

    > 绝对路径: 

    ~~~
    $ cd /c/xxx/yy/zzz
    ~~~

    > cd 常见用法

    ~~~
    // 返回根目录（ / ）
    $ cd /

    // 返回家目录（Linux中一般为：/home/UserName）
    $ cd ~

    // 返回上级目录
    $ cd ..

    // 返回上上级目录
    $ cd ../..

    // 返回上一次目录
    $ cd -
    ~~~

* history 查看历史命令
    ~~~
    // 查看输入历史命令
    $ history
    ~~~

* clear 清屏
    ~~~
    // 清屏
    $ clear
    ~~~

* tree 以目录树的方式显示信息
    ~~~
    $ tree /
    ~~~

* mv 剪切

* cp 复制文件/文件夹 ( -r )

> 命令格式：
~~~
命令	[参数]	[选项]
ls
touch	1.txt		
rm	xxx	-r
~~~

