title: 使用Hexo在github上搭建博客
date: 2013-12-01 15:00:00
categories: github
tags: [github, hexo, 博客]
---
在github上建立个人网站越来越容易，从jeklly到otcopress，直到现在的hexo，使得博客从建立越来越便利。github博客优点多多，如网站稳定，可以绑定域名等，最关键的是，没有关键字屏蔽（国内朋友经常遇到），因此，我义无反顾的加入了这个自由的世界。

github上的网站最初的目的是为项目提供一个简单的介绍网站，但是很多开发者将其作为个人的博客站点。当前github为个人、项目博客提供了两种不同的网址方式，使用hexo搭建博客的过程稍有不同，因此本文将分别介绍这两种方法。一是地址为username.github.io的个人博客，第3节介绍；二是地址为username.github.io/repo_name的项目网站，第4节介绍。<!--more-->

##1. 前提条件##
已经在github上注册账号，用户名假设为username。

##2. 配置环境##
###2.1 安装Git###
下载 [msysgit](http://code.google.com/p/msysgit/) 并执行即可完成安装。
###2.2 安装Node.js###
在 Windows 环境下安装 Node.js 非常简单，仅须下载[Node.js](http://nodejs.org/)安装文件并执行即可完成安装。
###2.3 安装hexo###
利用 npm 命令即可安装。（当[msysgit](http://code.google.com/p/msysgit/) 安装完毕，在任意位置点击鼠标右键，选择Git bash）

    npm install -g hexo
##3. 搭建个人博客##
###3.1 初始化hexo###
安装完成后，在你喜爱的文件夹下（如H:\hexo），执行以下指令(在H:\hexo内点击鼠标右键，选择Git bash)，Hexo 即会自动在目标文件夹建立网站所需要的所有文件。

    1	hexo init

现在我们已经搭建起本地的hexo博客了，执行以下命令(在H:\blog)，然后到浏览器输入[localhost:4000](localhost:4000)看看。

    1. hexo generate
    2. hexo server
好了，至此，本地博客已经搭建起来了，只是本地哦，别人看不到的。下面，我们要部署到Github。
###3.2 github上创建repository###
在自己Github主页右上角，创建一个新的repository。比如我的Github账号是wanderknight，那么我应该创建的repository名字应该是wanderknight.github.io。
###3.3 部署hexo项目到github###
编辑_config.yml(在H:\hexo下)。你在部署时，要把下面的wanderknight都换成你的账号名即username。

    deploy:
      type: github
      repository: https://github.com/wanderknight/wanderknight.github.io.git
      branch: master
执行下列指令即可将本地的hexo生成的静态html代码部署到github。

    1. hexo generate
    2. hexo deploy
Okay,我们的博客已经完全搭建起来了，十分钟后，在浏览器访问wanderknight.github.io就能看到你的成就了！

##4. 搭建项目网站##
###4.1 初始化hexo###
流程同3.1节。
###4.2 github上创建repository###
流程同3.2节，需要注意应该创建的repository名字创建的项目网站以后访问的时候是通过wanderknight.github.io/repo_name来访问。以前github的网站访问是.com的后缀，据说为了安全现在都改成了.io的后缀。
###4.3 部署hexo项目到github###
流程同3.3节。但一定要注意的不同是，分支branch设置为gh-pages，github通过这个分支来识别项目里哪些是网站的内容。

    deploy:
      type: github
      repository: https://github.com/wanderknight/repo_name.git
      branch: gh-pages

在浏览器访问wanderknight.github.io/repo_name就能看到你的项目网站了！
#5. 关于博客管理#
hexo上传到github上的博客内容都是hexo生成的静态网站，但是hexo项目本身的配置信息及你书写的markdown格式的博客内容都仅仅在本地保存；因此，我又在github上创建了个repository称之为blog，并将个人及项目博客加入到这个blog项目。
#6. 其他事项#
注意：有些新用户需要设置 ssh，否则上述命令会失败。ssh 的介绍和设置方法请看官方教程，不用担心，很简单。

记住：每次修改本地文件后，需要hexo generate才能保存。每次使用命令时，都要在H:\hexo目录下。