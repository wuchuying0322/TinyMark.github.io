---
title: Linux学习笔记（二）
tags: Linux
categories: 
- Linux
- 学习笔记
---

# 常用基础操作命令
* \> or >> 重定向：
> 相同点：如果文件不存在，那么就新建

    > 不同点：
    > * \> 如果文件之前存在，那么就覆盖
    > * \>> 如果文件之前存在，那么就是 追加
~~~
 // 将当前目录内容（覆盖）保存到 重定向文件.txt 文件 中
 $ ls > 重定向文件.txt
 
 // 将当前目录内容（追加）保存到 重定向文件.txt 文件 中
 $ ls >> 重定向文件.txt
~~~

* gedit 编辑器
~~~ 
// 使用 gedit 编辑器 查看或修改xxx.txt文件
$ gedit xxx.txt 
~~~

* cat 查看文件的内容（一次性显示所有的内容）
~~~
// 在终端内显示 xxx.txt 的内容
$ cat xxx.txt
~~~

* more 分屏显示文件的内容
~~~
// 在终端内部分屏显示 xxx.txt 的内容
$ more xxx.txt
~~~

* 常见用法：
~~~
$ ls / -alh | more 
// 先执行ls / -alh 把内容存储到 管道(|)中
// 然后more命令从管道(|)中取数据，然后分页显示

$ cat a.txt b.txt > c.txt 
// 合并文件 a.txt 和 b.txt 存储到 c.txt 中
~~~

* grep 从文件中 搜索内容
~~~
// 从文件中 搜索内容
$ grep
~~~

* find 从某个路径中 搜索文件
~~~
// 从某个路径中 搜索文件
$ find 
~~~


# 打包与压缩等
* 常见命令

    tar     打包

    gzip    用 gzip 压缩

    bzip2   用 bzip2 压缩

* 常见选项

     -c     归档文件

     -x     压缩文件

     -z     gzip压缩文件

     -j     bzip2压缩文件

     -v     显示压缩或解压缩过程 v(view)

     -f     使用档名

* 打包与解包
~~~
// 将 *.txt 打包 成为 xxx.tar
$ tar -cvf xxx.tar  *.txt

// 将 xxx.tar 解包
$ tar -xvf xxx.tar  
~~~

* 压缩与解压缩
~~~
// 将 xxx.tar 压缩 成 xxx.tar.gz 
$ gzip xxx.tar  

// 将 xxx.tar.gz 解压缩
$ gzip -d xxx.tar.gz
~~~

* 混合操作
~~~
// 将 xxx.txt 打包并用 gzip 压缩
$ tar -zcvf xxx.tar.gz xxx.txt 

// 将 xxx.tar.gz 用 gzip 解压缩并解包
tar -zxvf xxx.tar.gz 
~~~
~~~
// 将 xxx.txt 打包并用 bzip2 压缩
tar -jcvf xxx.tar.bz2 xxx.txt

// 将 xxx.tar.bz2 用 bzip2 解压缩并解包
tar -jxvf xxx.tar.bz2
~~~

系统管理命令

> useradd 添加用户

> userdel 删除用户

> su 切换用户

> exit 退出用户

> ssh python@192.168.106.81 远程登录

> who 查看当前登录的用户

> whoami 查看当前用户


> ifconfig 查看网卡信息、修改等


> sudo 用超级管理员的权限执行命令


> chmod 修改文件权限








