---
title: SSH 配置方法
tags: SSH
date: 2017-03-05
categories: 奇技淫巧
---
> Git是分布式的代码管理工具，远程的代码管理是基于SSH的，
所以要使用远程的git则需要SSH的配置。

# 单个密钥配置方法
1. 查看是否有 SSH 密钥
> 输入 cd ~/.ssh
~~~
$ cd ~/.ssh
~~~
    > 如果没有密钥则不会有此文件夹，
    如图：
    ![image](/image/ssh_1-1.png)
    有则备份删除

2. 生成密钥
> 输入 ssh-keygen -t rsa -C "YourEmail@XXX.com"
~~~
$ ssh-keygen -t rsa -C "YourEmail@XXX.com"
~~~
    > 提示输入信息，不用管，连续敲 3 个回车
    结果如图：
    > ![image](/image/ssh_1-2.png)

3. 与 Github 进行关联
* 复制公钥
> 进入 C:\Users\UserName\.ssh 目录
用 记事本 打开 id_rsa.pub 文件
先全选，然后复制里面所有的内容
> ![image](/image/ssh_1-3.png)

* 保存到 Github 
> 登陆你的 Github ，点击 Settings
> ![image](/image/ssh_1-4.png)
> 选择左侧 SSH and GPG keys 选项
> ![image](/image/ssh_1-5.png)
> 点击 New SSH key 按钮
> ![image](/image/ssh_1-6.png)
> 在 Title 中随便写一个名字
再在 Key 中粘贴刚才复制的文本内容
> ![image](/image/ssh_1-7.png)
> 添加完成！
> ![image](/image/ssh_1-8.png)


<!-- # Github 配置 SSH -->
