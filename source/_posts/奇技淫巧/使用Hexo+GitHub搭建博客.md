---
title: 使用 Hexo+Github 搭建博客
tags: [Hexo,博客]
date: 2017-03-08
categories: 奇技淫巧
---

# Hexo
## 安装 Node.js
> 根据个人电脑版本（64或32位）
[下载NodeJS](http://nodejs.cn/download/)
> 建议选择 <b>LTS版本</b> | [参考文档](http://www.runoob.com/nodejs/nodejs-install-setup.html)

## 安装 Git
> 根据个人电脑版本（64或32位）
[下载 Git](http://git-scm.com/download/)

<!-- more --> 

## 安装Hexo
1. 新建文件夹'myBlog' 并进入
2. 在空文件夹内单击 ‘鼠标右键’，选择 ‘Git Bash Here’
![Git Bash Here](/image/hexo_3-2.png)
3.弹出小黑窗 
![黑窗](/image/hexo_3-3.png)
> 在黑窗中，按顺序输入下面代码
    ~~~ 
    $ npm i hexo-cli -g
    $ hexo init blog    // 根据个人网速情况，可能要等很久
    $ cd blog
    $ npm i     // 根据个人网速情况，可能要等很久
    $ hexo g
    $ hexo s
    ~~~

4. 在浏览器输入：http://localhost:4000/ 查看
![Git Bash Here](/image/hexo_3-4.png)

## 配置主题（可选）
### [NexT主题](http://theme-next.iissnan.com/)
1. 下载主题：
    1. 进入你博客目录中，如 'blog' 文件夹中
    2. 在文件夹内单击 ‘鼠标右键’，选择 ‘Git Bash Here’
![Git Bash Here](/image/hexo_4-1.png)    
    3. 在黑窗中，输入下面代码
    ~~~
    $ git clone https://github.com/iissnan/hexo-theme-next themes/next 
    // 根据个人网速情况，可能要等很久
    ~~~
    ![Git Bash Here](/image/hexo_4-2.png)        
2. 启用主题
    1. 找到 '~/myBlog/blog/_config.yml' 文件
    2. 第75行改为 
    ~~~ 
    theme: next
    ~~~
    ![Git Bash Here](/image/hexo_4-3.png)

3. 主题设定
    > 详见 [NexT/#theme-settings](http://theme-next.iissnan.com/getting-started.html#theme-settings)

## 完成部署GitHub

1. 继续在黑窗，安装部署工具
    ~~~
    $ npm i hexo-deployer-git --save
    ~~~
    ![Git Bash Here](/image/hexo_5-1.png)

2. 找到 '~/myBlog/blog/_config.yml' 文件，修改最后的代码：
    ~~~
    deploy:
    type: git
    repo: git@github.com:yourName/yourName.github.io.git
    branch: master
    ~~~
    ![Git Bash Here](/image/hexo_5-2.png)
    
## 总结常用命令
~~~
$ hexo clean 
// 清空 hexo generate 生成的博客

$ hexo g （hexo generate） 
// 生成博客文件

$ hexo s （hexo server）
// 启动本地服务器

$ hexo d （hexo deploy）
// 按照配置好的_config.yml文件，完成部署
~~~