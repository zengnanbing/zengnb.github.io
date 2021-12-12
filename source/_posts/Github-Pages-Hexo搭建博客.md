---
title: Github-Pages-Hexo搭建博客
date: 2017-03-20  16:32:31
tags:
ategories: 工具
---

### 第一部分

#### GitHub Pages是什么？

GitHub Pages本用于介绍托管在GitHub的项目， 不过，由于他的空间免费稳定，用来做搭建一个博客再好不过了。

#### 接下来应该怎么做？

Hexo 是一个简单地、轻量地、基于Node的一个静态博客框架，可以方便的生成静态网页托管在github。我们要使用Github Pages + Hexo搭建博客站点，就必须注册Github账号，安装git、node.js以及hexo等，接下来就一起来实践吧！

#### Github注册与配置

##### 注册

如果你还没有自己的Github账号，那请到Github官网注册账号：https://github.com/

注册成功后github会发送验证邮件到你的邮箱，请查收邮件并进行验证。

##### 新建版本库

注册完成后，点击Start a project来新建一个版本库。

如果你已经注册，则在自己的主页，点击”New repository”，输入Repository name:yourname.github.io(yourname与你的注册用户名一致,这个就是你博客的域名了)

![](D:\study\blog\source\_posts\images\工具\博客搭建1.png)

##### 启用GitHub Page

进入版本库后，点击右上方的setting，下来到Githubs pages栏目

![](D:\study\blog\source\_posts\images\工具\博客搭建2.png)

![image-20211212135139894](C:\Users\zeng\AppData\Roaming\Typora\typora-user-images\image-20211212135139894.png)

这里看到博客的访问地址，指定博客源文件的分支，设置自己的个人域名

#### 下载并安装Git

根据自己电脑操作系统的位数到git官网下载相应的版本：

https://git-scm.com/download/win

安装与配置过程可参考图文教程：[git的安装和配置](http://jingyan.baidu.com/article/9f7e7ec0b17cac6f2815548d.html)

SSH-KEY的生成与配置可参考图文教程[window下配置SSH连接GitHub、GitHub配置ssh key：](http://jingyan.baidu.com/article/a65957f4e91ccf24e77f9b11.html)

#### 下载并安装node.js

根据自己电脑操作系统的位数到git官网下载相应的版本：

https://nodejs.org/en/download/

##### 测试是否安装成功

命令提示符窗口，输入如下命令：

![](D:\study\blog\source\_posts\images\工具\博客搭建4.png)

#### 安装Hexo

在合适的地方新建一个文件夹，用来存放自己的博客文件，比如我的博客文件都存放在`D:\study\blog`目录下。

在该目录下右键点击`Git Bash Here`，打开git的控制台窗口，以后我们所有的操作都在git控制台进行，就不要用Windows自带的控制台了。

定位到该目录下，输入`npm i hexo-cli -g`安装Hexo。会有几个报错，无视它就行。

安装完后输入`hexo -v`验证是否安装成功。

然后就要初始化我们的网站，输入`hexo init`初始化文件夹，接着输入`npm install`安装必备的组件。

这样本地的网站配置也弄好啦，输入`hexo g`生成静态网页，然后输入`hexo s`打开本地服务器，然后浏览器打开[http://localhost:4000/](https://link.zhihu.com/?target=http%3A//localhost%3A4000/)，就可以看到我们的博客啦，效果如下：

![](D:\study\blog\source\_posts\images\工具\博客搭建5.png)

打开博客根目录下的`_config.yml`文件，这是博客的配置文件，在这里你可以修改与博客相关的各种信息。

修改最后一行的配置：

```bash
deploy:
  type: git
  repository: https://github.com/zengnanbing/zengnanbing.github.io
  branch: master
```

repository修改为你自己的github项目地址。

##### 安装hexo-deployer-git插件

```
$ npm install hexo-deployer-git --save
```

##### 部署到Github上

依次执行以下三条命令：

```
$ hexo clean  #清除缓存 网页正常情况下可以忽略此条命令
$ hexo generate  #生成静态页面至public目录
$ hexo deploy  #将.deploy目录部署到GitHub
```

执行hexo deploy命令之后，如果最后一行打印出如下信息则表示部署成功

```
INFO  Deploy done: git
```

然后你再去访问你创建的Github pages地址，也就是：你的Github用名.github.io，即可看到你本地的hexo项目已经被部署到github上去了。此时博客的默认主题是landscape，即上面本地测试时的样子。