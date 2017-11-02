---
title: Git 使用小技巧
tags: Git
date: 2017-03-05
categories: 杂
---

# 利用 批处理(bat)文件 一键推送 Git

> 当我们使用 Git 向远端仓库提交代码的时候，每次都需要输入很多条 git 命令（至少3条）
如：
~~~
$ git add 需要提交的文件
$ git commit -m '提交信息'
$ git push 远端仓库地址 分支名
~~~

寻思可否简化一下，利用 批处理(bat)文件 来直接操作
> 当然可以使用 Git 自带的 GUI 或者 TortoiseGit 软件，这里暂不讨论

1. 进入 Git 的安装目录中的 cmd 文件夹，默认路径是 C:\Program Files\Git\cmd 

2. 在此创建一个 xxx.bat 文件，如果没有权限，可以在桌面创建完再拖进来，需要管理员权限

3. 点击右键编辑，输入以下代码
~~~
@echo off

cd /d Git控制的文件夹路径
% 如：C:\Users\Administrator\Desktop\myCode %

git status
@echo 按任意键确认上述状态并提交，按 Ctrl+C 退出
pause>nul

git add 需要提交的文件
git commit -m '提交信息'
git push 远端仓库地址 分支名

@echo 提交完成，按任意键退出
pause>nul
exit
~~~
    完成后保存并退出

4. 右键发送到桌面快捷方式
> 这样下次直接双击就行了