---
title: （一）使用 Hexo+Github 搭建博客
tags: [Hexo,博客]
date: 2017-03-08
categories: 奇技淫巧
---

# Hexo介绍
> [hexo](https://hexo.io/zh-cn/) —— 快速、简洁且高效的博客框架
    ![image](/image/hexo_1-1.png)

# 安装 Node.js
> 根据个人电脑版本（64或32位）
[下载NodeJS](http://nodejs.cn/download/)
> 建议选择 <b>LTS版本</b> | [参考文档](http://www.runoob.com/nodejs/nodejs-install-setup.html)

# 安装 Git
> 根据个人电脑版本（64或32位）
[下载 Git](http://git-scm.com/download/)

<!-- more --> 

# 安装Hexo
1. 新建文件夹'blog' 并进入

2. 在空文件夹内单击 ‘鼠标右键’，选择 'Git Bash Here'
![image](/image/hexo_3-2.png)

3. 弹出 bash 小黑窗 
![image](/image/hexo_3-3.png)
    * 在黑窗中，按顺序输入下面代码
    1. 输入 npm i -g hexo-cli ，使用 npm 全局安装 hexo 的命令行工具
        ~~~ 
        $ npm i -g hexo-cli     
        ~~~
    2. 输入 hexo init  ，利用 hexo 命令初始化一个新的博客
        ~~~
        $ hexo init     // 根据个人网速情况，可能要等很久
        ~~~
        > 初始化中...
        ![image](/image/hexo_3-3-0.png)    

        > hexo init 初始化完成！
        ![image](/image/hexo_3-3-1.png)   
    3. 输入 npm i ，安装包（如果网速差或报错，建议使用 cnpm ）
        [cnpm 的使用方法](https://npm.taobao.org/)
        ~~~
        $ cnpm i     // 根据个人网速情况，可能要等很久
        ~~~
        > 使用 cnpm i 安装包
        ![image](/image/hexo_3-3-2.png)
        
    4. 输入 hexo s ，开启本地服务器
        ~~~
        $ hexo s
        ~~~
        ![image](/image/hexo_3-4-1.png)

    5. 在浏览器输入：http://localhost:4000/  查看我们的博客
        ![image](/image/hexo_3-4.png)

# 写博客
> 把写好的 markdown 文件，存放到 /source/_posts 文件夹 中即可

# 配置 NexT 主题（可选）
## Made by [IIssNan](https://github.com/iissnan) @ GitHub

* NexT 主题官方文档： [http://theme-next.iissnan.com/](http://theme-next.iissnan.com/)
* 具体配置参考： [NexT主题基本配置](https://tinymark.github.io/2017/03/06/奇技淫巧/NexT主题基本配置)

# 完成部署GitHub
> 原理：
每个 Github 账户都可以创建一个 YourName.github.io 的仓库，
这个仓库的 master 分支是可以直接使用 YourName.github.io 在网络中访问的，
我们可以利用 Github 的这个功能来进行静态页面的展示。

> 有两种部署的方式，一种是手动部署，一种是使用 hexo 命令行部署，推荐使用第二种

## 1. 手动部署
1. 清空之前生成的博客文件
    > 进入 bash 小黑窗，输入 hexo clean （如果服务器开启中，可以使用 Ctrl + c 停止）
    ![image](/image/hexo_2-2.png)    

2. 生成博客文件
    > 输入 hexo g
    ~~~
    $ hexo g
    ~~~
    > 生成完成！
    ![image](/image/hexo_2-3.png)    
    
3. 进入 public 文件夹中，开启 bash 黑窗
    > 进入 public 文件夹
    ![image](/image/hexo_2-4.png)    
    > 开启 bash 黑窗
    ![image](/image/hexo_2-5.png)    

4. 输入git init 初始化仓库，并使用 add 和 commit 提交
    ~~~
    $ git init
    $ git add .
    $ git commit -m 'blog'
    ~~~
    > git init & git add .
    ![image](/image/hexo_2-7.png)   
    > git commit
    ![image](/image/hexo_2-8.png)   
    > 完成提交！
    ![image](/image/hexo_2-9.png)                       

5. 使用 git push 命令推送到 Github 仓库
    > 注意后面需要加上 --force 强制覆盖
    ~~~
    $ git push https://github.com/YourName/YourName.github.io.git master --force
    ~~~
    > 如果使用 https 地址，需要输入用户名和密码
    ![image](/image/hexo_2-10.png)                       
    > 推送完成！
    ![image](/image/hexo_2-11.png)                       

6. 在浏览器输入 YourName.github.io 来访问你的博客
    ![image](/image/hexo_2-12.png)                       

## 2. 使用 hexo 命令部署
* 此方法需要配置 SSH 密钥来免密提交，SSH 的配置方法参考 [SSH配置方法](https://tinymark.github.io/2017/03/06/奇技淫巧/NexT主题基本配置/)

1. 在 blog 文件夹中打开 bash 黑窗，安装部署工具
    ![image](/image/hexo_5-0.png)  
    > 输入 npm i hexo-deployer-git --save  来安装 hexo 部署工具
    ~~~
    $ npm i hexo-deployer-git --save
    ~~~
    > 同样可以使用 cnpm 进行安装（推荐）
    ![image](/image/hexo_5-1.png)

2. 找到 '~/blog/_config.yml' 文件，修改最后的代码：
    > 代码如下：
    ~~~
    deploy:
        type: git
        repo: git@github.com:YourName/YourName.github.io.git
        branch: master
    ~~~
    > ![image](/image/hexo_5-2.png)

3. 清空之前生成的博客文件
    > 打开 bash 小黑窗
    > 输入 hexo clean 
    > ![image](/image/hexo_5-3.png)

4. 生成博客文件
    > 输入 hexo g
    ~~~
    $ hexo g
    ~~~
    > 生成完成！
    ![image](/image/hexo_2-3.png)  

5. 部署到 Github
    > 输入 hexo d 
    ~~~
    $ hexo d
    ~~~
    > 最后显示 INFO  Deploy done: git 代表部署成功
    > ![image](/image/hexo_5-4.png)
    
6. 在浏览器输入 YourName.github.io 来访问你的博客
    ![image](/image/hexo_2-12.png)  

# 自动部署方案
> [使用Travis CI自动部署Hexo博客](https://tinymark.github.io/2017/03/06/奇技淫巧/使用Travis CI自动部署Hexo博客)

# 总结常用命令
~~~
$ hexo clean 
// 清空 ( hexo generate ) 生成的博客

$ hexo g （hexo generate） 
// 生成博客文件

$ hexo s （hexo server）
// 启动本地服务器

$ hexo d （hexo deploy）
// 按照配置好的_config.yml文件，完成部署
~~~