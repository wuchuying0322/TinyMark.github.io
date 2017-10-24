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


# 配置多个key

1. 依次生成多个密钥
> 输入 ssh-keygen -t rsa -C "YourEmailN@XXX.com" -f ~/.ssh/id_rsa_NameN
~~~
$ ssh-keygen -t rsa -C "YourEmail1@XXX.com" -f ~/.ssh/id_rsa_Name1

$ ssh-keygen -t rsa -C "YourEmail2@XXX.com" -f ~/.ssh/id_rsa_Name2
~~~

2. 复制公钥到对应的远端仓库
> 进入 C:\Users\UserName\.ssh 目录
* 用 记事本 打开 id_rsa.pub 文件
* 全选，复制，保存到远端仓库

3. 配置config
> 在 ~/.ssh 目录下添加 config配置文件 用于区分多个SSH-Key
* 进入 C:\Users\UserName\.ssh 目录
* 新建一个 config 文件，无后缀名，内容如下：
~~~
    Host Name1
        HostName github.com
        PreferredAuthentications publickey
        IdentityFile ~/.ssh/id_rsa_Name1
        User Name1

    Host Name2
        HostName github.com
        PreferredAuthentications publickey
        IdentityFile ~/.ssh/id_rsa_Name2
        User Name2
~~~
* Host 是git使用ssh提交时 @ 的地址（默认为远端仓库地址，为了同时使用多个key，我们使用 keyName 来区分）
* HostName 是对应的远端仓库地址
* IdentityFile 是私钥的本地路径
* User 是远端仓库的用户名

4. 使用 ssh 提交时需要注意
* 在使用 git push url branch 命令进行免密提交时，url例：git@github.com:YourName/test.git 中，@符号的github.com 需要替换成对应的 Host

5. 可以设置 origin 
