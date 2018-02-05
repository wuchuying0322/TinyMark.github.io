---
title: Git使用总结
tags: Git
categories: 
- 杂
- GIT
---

# Git是什么？

Git是世界上最先进的分布式版本控制系统，没有之一。

# 创建版本库
    如果使用Windows系统，为了避免遇到各种莫名其妙的问题，请确保目录名（包括父目录）不包含中文。
    
<!-- more --> 

初始化一个Git仓库

	$ git init

添加文件到Git仓库，分两步：
	
	$ git add readme.txt
	
	$ git commit -m "first commit"

# 版本控制
查看仓库当前（工作区）的状态

	$ git status
	
查看修改的内容

	$ git diff

## 版本回退

查看历史记录 （以便确定要回退c到哪个版本）

	$ git log

查看命令历史记录 （以便确定要回到未来的哪个版本）
	
	$ git reflog

回退上一个版本

	$ git reset --hard HEAD^

回退某个历史版本

	$ git reset --hard SHA

## 理解 工作区 、暂存区 和 版本库

### 工作区（Working Directory）

    你在电脑里，看到的项目目录

### 版本库（Repository）

    工作区中有一个隐藏目录.git，这个不算工作区，而是Git的版本库

### 暂存区（Stage）

版本库中有暂存区

git add 命令实际上就是把要提交的所有修改放到 暂存区

## 管理修改

Git比其他版本控制系统设计得优秀，因为Git跟踪并管理的是修改，而非文件

操作过程：

    第一次修改 -> git add -> 第二次修改 -> git add -> git commit

## 撤销修改

把fileName文件在工作区的修改全部撤销

    $ git checkout --fileName
          (检出)

总之，就是让这个文件回到最近一次 git commit 或 git add 时的状态    

git checkout 其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”

## 删除文件

工作区中删除文件

    $ rm fileName

此时你有两个选择，一是确实要从版本库中删除该文件，那就用命令git rm删掉，并且git commit

    $ git rm fileName
    $ git commit -m "remove fileName"

另一种情况是删错了，你可以把误删的文件恢复到最新版本

    $ git checkout --fileName
