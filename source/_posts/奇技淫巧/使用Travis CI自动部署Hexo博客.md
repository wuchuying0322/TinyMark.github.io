---
title: 使用 Travis CI 自动部署 Hexo 博客
tags: [Travis CI,博客]
date: 2017-03-08
categories: 奇技淫巧
---

# 使用 Travis CI 自动部署 Hexo 博客
## CI 持续集成
> 持续集成：Continuous Integration，简称CI，意思是，在一个项目中，任何人对代码库的任何改动，都会触发CI服务器自动对项目进行构建，自动运行测试，甚至自动部署到测试环境。

<!-- more --> 

## Travis CI 是个啥
[Travis CI](https://travis-ci.org/) 是在线托管的CI服务，用Travis来进行持续集成，不需要自己搭服务器，在网页上点几下就好，用起来更方便。最重要的是，它对开源项目是免费的。

参考 [使用Travis进行持续集成 —— by廖雪峰老师](https://www.liaoxuefeng.com/article/0014631488240837e3633d3d180476cb684ba7c10fda6f6000)

## 思路
> 当我们使用 hexo + Github 搭建博客，每次更新内容的时候，都很麻烦，需要下面几个步骤：
* hexo g 生成博客文件
* 进入 public 文件夹，把内容推送到远端 Github 的 xxx.github.io 仓库 master 分支

> 虽然 hexo 集成了部署功能，但是这样无法把我们博客的代码托管到 GitHub 中，代码还是需要存在本地
* 配置好_config.yml文件的deploy
* hexo d 部署到远端仓库

> 所以，我们利用 Travis CI 进行自动部署。
原理是：我们把源代码放在 io仓库 的 hexo 分支中，再将 hexo分支 交给 Travis 进行托管，这样我们每次更新内容向 io仓库 的 hexo 分支提交的时候，Travis 就会帮我们自动进行构建和部署
* 选择 Travis 需要托管的 GitHub 仓库
* 本地配置 .travis.yml 文件
* 向 GitHub 仓库目标分支提交更新
* Travis 会根据配置文件自动进行构建部署

## 使用步骤
1. 登陆[Travis CI (https://travis-ci.org/)](https://travis-ci.org/)与Github进行关联
![image](/image/travis_1-0.png)
![image](/image/travis_1-1.png)
2. 授权 Travis ，托管需要自动部署的仓库
![image](/image/travis_1-2.png)
![image](/image/travis_1-3.png)
3. 设置选项
![image](/image/travis_1-4.png)
> 此时，Travis 已经接管你Github这个仓库里的代码了，一旦线上仓库有变动，Travis就会自动进行构建部署。

但是现在还有两个问题：
> 1. 我们需要在 Github 生成密钥交给 Travis ，以便 Travis 构建后进行自动部署
> 2. 我们还需要在本地配置 .travis.yml 文件，然后再推送到远端仓库才行

4. 在 Github 生成密钥
    1. 进入 Github 设置
    ![image](/image/travis_1-6.png)
    2. 点击 Personal access tokens
    ![image](/image/travis_1-7.png)
    3. 新建一个新安全令牌
    ![image](/image/travis_1-8.png)
    4. 写上令牌名称，勾选下面所有选项，除了delete_repo
    ![image](/image/travis_1-9.png)
    5. 点击复制生成的密钥
    ![image](/image/travis_1-10.png)
    6. 回到 Travis 设置选项中，填写密钥
    > 注意 key 写 GH_TOKEN ，复制密钥，点击 Add
    ![image](/image/travis_1-11.png)
    7. 最后添加的结果
    ![image](/image/travis_1-12.png)

5. 本地配置 .travis.yml 文件
在博客根目录创建一个名为 .travis.yml 的文件
![image](/image/travis_1-13.png)
内容如下：
~~~ yml
language: node_js
node_js: stable

# S: Build Lifecycle
install:
  - npm i

cache:
  directories:
    - "node_modules"

#before_script:
 # - npm install -g gulp

script:
  - hexo g

after_script:
  - cd ./public
  - git init
  - git config user.name "YourUserName"
  - git config user.email "YourEmail@gmail.com"
  - git add .
  - git commit -m "Update docs"
  - git push --force --quiet "https://${GH_TOKEN}@${GH_REF}" master:master
# E: Build LifeCycle

branches:
# your branches
  only:
    - hexo

env:
 global:
   - GH_REF: github.com/YouName/YouName.github.io.git
~~~

5. 修改user.name、user.email、GH_REF
> user.name：   你 Github 的 用户名
> user.email：  你 Github 的 Email
![image](/image/travis_1-14.png)
> GH_REF：    你 GitHub io仓库的地址
![image](/image/travis_1-15.png)

6. 更新代码到 Github 仓库的 hexo 分支
    1. 进入 /hexo/themes/next 文件夹，删除 .git 文件夹，否则会导致 主git无法管理主题文件
    2. 在 hexo 根目录初始化一个新仓库
    ~~~
    $ git init
    ~~~
    ![image](/image/travis_2-1.png)
    3. 切换到 hexo 分支
    ~~~
    $ git checkout -b hexo
    ~~~
    ![image](/image/travis_2-2.png)    
> 提交代码
~~~ 
$ git checkout -b hexo
$ git add .
$ git commit -m 'first commit'
$ git push git@github.com:YourName/YourName.github.io.git hexo
~~~

7. 等待 Travis 构建完成
![image](/image/travis_2-3.png)

8. 成功构建完成的结果
![image](/image/travis_2-4.png)    

* 完成后，我们进入 YourName.github.io 搂一眼结果
> Oye!It's working！
    ![image](/image/travis_2-5.png)    

* 下次更新的时候，直接往 Github 的 io仓库 hexo 分支中提交代码就行了