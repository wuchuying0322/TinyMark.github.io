---
title: （二）NexT 主题的基本配置
tags: [Hexo,博客]
date: 2017-03-07
categories: 
- 杂
- 博客
---

# [NexT主题](http://theme-next.iissnan.com/)

## 作者
* Made by [IIssNan](https://github.com/iissnan) @ GitHub

## 官方文档
* [http://theme-next.iissnan.com/](http://theme-next.iissnan.com/)

# 下载主题
1. 进入你博客 根目录 中，如 'blog' 文件夹中
2. 在文件夹内单击 ‘鼠标右键’，选择 ‘Git Bash Here’，打开 bash 黑窗
    > ![image](/image/hexo_5-0.png)    
3. 克隆主题文件
    > 输入 git clone https://github.com/iissnan/hexo-theme-next themes/next
    ~~~
    $ git clone https://github.com/iissnan/hexo-theme-next themes/next 
    // 根据个人网速情况，可能要等很久
    ~~~
    > ![image](/image/hexo_4-1.png)        

# 启用主题
> 找到 ~/blog/_config.yml 文件
第75行改为 
~~~ 
theme: next
~~~
> ![image](/image/hexo_4-3.png)

# 主题设置
> 官网文档 [NexT/#theme-settings](http://theme-next.iissnan.com/getting-started.html#theme-settings)

# 设置语言
> 找到 ~/blog/_config.yml 文件
第10行改为 
~~~ 
language: zh-Hans
~~~
> ![image](/image/next_1-0.png)

## 选择外观
NexT 主题提供 3 种外观：
* Muse - 默认 Scheme，这是 NexT 最初的版本，黑白主调，大量留白
* Mist - Muse 的紧凑版本，整洁有序的单栏外观
* Pisces - 双栏 Scheme，小家碧玉似的清新

以 Pisces 外观为例：
> 找到 ~/blog/themes/next/_config.yml 文件
注释掉第72行，
放开第74行注释，
改如下图：
> ![image](/image/next_1-1.png)

## 设置头像
> 找到 ~/blog/themes/next/_config.yml 文件
放开第114行注释，
改如下图：
> ![image](/image/next_1-9.png)
> 路径对应图片更改一下
> ![image](/image/next_1-10.png)

## 设置菜单
1. 改 next 主题 的配置文件
> 找到 ~/blog/themes/next/_config.yml 文件
修改第 53 行 
放开第 55、56、57 行注释，
改如下图：
> ![image](/image/next_1-2.png)

2. 关联文件
> 在 blog 根目录，打开 bash 黑窗
输入 hexo new page "categories"
输入 hexo new page "tags"
~~~
$ hexo new page "categories"
$ hexo new page "tags"
~~~
    > 会对应生成两个文件夹，里面包含一个 index.md 的文件
    > ![image](/image/next_1-3.png)    
    > 分别进入两个 index.md 文件中
改如下图：
> ![image](/image/next_1-4.png)
> ![image](/image/next_1-5.png)

3. 写博客
    > * 写一个博客页面
    > 在 ~/blog/source 目录中，
    新建一个 test.md 文件
    在头部加入下面代码：
    ~~~
    ---
    title: title
    tags: tags
    categories: categories
    date: yyyy-mm-dd
    ---
    ~~~
    > 例如下图：
    > ![image](/image/next_1-6.png)

    > * 开启 hexo 服务器
        > 输入 hexo s ，开启本地服务器
        ~~~
        $ hexo s
        ~~~
    > * 在浏览器输入：http://localhost:4000/  进入博客
    > 点击 左侧边栏—分类，查看是否关联成功
    > ![image](/image/next_1-7.png)
    博客文件头部 对应的参数
    > ![image](/image/next_1-8.png)    

# 设置侧边栏
> 找到 ~/blog/_config.yml 文件
第 6、7、8、9 行，参数改为 
~~~ 
title: this is title
subtitle: this is subtitle
description: this is description
author: this is author
~~~
改如下图：
> ![image](/image/next_1-11.png)
参数对应页面的位置
> ![image](/image/next_1-12.png)
