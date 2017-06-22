---
title: Hello Hexo
date: 2017/6/14 1:42:25
tags:
- 技术
- 教程
categories: 技术
---

**快速开始**
===

欢迎来到此博客，下面我介绍下用到的技术：

- 基于nodejs语言的快速、便捷的轻量级框架[hexo](https://github.com/hexojs/hexo),star数接近了两万人数；
- 需要安装nodejs的环境和git环境；
- 需要注册[github](https://www.github.com)账号、密码；并且设置秘钥，这是基础的[git教程](http://www.liaoxuefeng.com/)

- 使用hosts或者vpn进行翻墙，主要是为了方便使用github；
- 需要取代记事本的文本编辑器，推荐[notepad++](https://notepad-plus-plus.org/)
- 一个符合自己个性的[域名](https://sg.godaddy.com/zh/)(非必要的)

<!-- more -->
以上就是应该准备的东西，下面我将此博客搭建完成的过程记录下来，涉及到三个方面：

**一、安装工作**
---

我主要参考了以下几个详细的博客：

1. [手把手教你用Hexo+Github 搭建属于自己的博客](http://blog.csdn.net/gdutxiaoxu/article/details/53576018)
2. [小白独立搭建博客--Github Pages和Hexo简明教程](https://my.oschina.net/ryaneLee/blog/638440)
3. [hexo初探——让写作飞起来](http://www.shellsec.com/news/35418.html)
4. [史上最浅显易懂的Git教程](http://www.liaoxuefeng.com/)

按照以上的教程，你最终会搭建出一个带有**next**主题的大气又不失逼格的博客。前提是你得懂一些git的基础操作和原理，不然对于初学者来说很是困难。

**二、主要难点**
---
- 命令的掌握：

1. **Hexo的命令：**
``` bash
#1. 新建博文
$ hexo new "标题"

#2.清除缓存
$ hexo clean

#3.本地调试
$ hexo s -g

#4.发布远端
$ hexo d -g
```

- **附加功能的添加**
1. [网易云音乐集成到任意页面](http://weqeo.com/2016/10/11/Hexo%E4%B8%AD%E6%92%AD%E6%94%BE%E7%BD%91%E6%98%93%E4%BA%91%E9%9F%B3%E4%B9%90%E7%9A%84%E5%AE%9E%E8%B7%B5/)
2. 文章分类、标签和关于我等页面的添加

> 原因是**next**主题默认没有设置*about*、*categoties*、*tags*页面；而要你自己去配置命令创建。

> 首先，要先执行下面的三个命令；

``` bash
#在hexo博客目录下执行命令:

#创建关于我页面
$ hexo new page "about"

#创建标签页面
$ hexo new page "tags"

#创建分类页面
$ hexo new page "categories"

```

> 其次，找到配置文件(_config.yml)设置 Menu Settings**取消掉tags、about、categories前面的注释符号‘#’**

> 最后，会发现**source** 文件夹下出现了about、tags等文件，里面有md格式的文件用于编辑。

3. 图片存储，使用七牛云存储，个人版免费，只需添加图片的地址类似这样添加

```
![图片名称](http://orwkfxzfh.bkt.clouddn.com/blog20170622235655.png)
```

4. markdown[格式](http://www.appinn.com/markdown/)、和md文件编辑器，这里我推荐颜值很高的[vscode](https://code.visualstudio.com/)
，所见即所得的优秀编辑器。左边编写页，右边视图页。


![vscode编辑器](http://orwkfxzfh.bkt.clouddn.com/blog20170622235655.png)

5. git的使用


**三、博客备份**
---
&emsp;&emsp;博客应该到此搭建成功了，最起码搭建成我的这个样子，剩下的要自己去看[文档](https://hexo.io/zh-cn/docs/)了；
最后，再分享下自己的备份策略吧(应该很重要，想象下博文全部丢了是什么感觉...)：

通过自己的发现我们发现我们所写的markdown格式的文章都保存在 `E:\hexo\source\_posts` 这个文件夹下，
我们的策略应该有以下的几种：
1. U盘、云盘拷贝存储
2. Git版本控制
3. Git分支控制
4. 其他软件
我采取的是第二中：Git文件对 `_posts` 这个文件夹进行版本控制：

__步骤如下:__  

1. 到[github](https://www.github.com)新建名称为`_posts`的仓库；直接点击`+`创建；
2. 接着gitbash进入本地的 `E:\hexo\source\_posts` 文件夹下，按顺序执行：
``` bash
#初始化git仓库
$ git init

#添加全部文件到暂存区
$ git add .

#提交到工作区
$ git commit -m '初始化仓库'

#添加远程版本库:复制
$ git remote add origin git@github.com:yourname/_posts.git

#推送本地的版本库到远程的master分支
$ git push origin master

```
3. 这样在第一次执行后，每一次编辑文章完成时就要先使用以上的命令(除过第一条)备份文件，然后再执行 `hexo d -g` 推送文章到自己的站点仓库；千万别弄错了顺序。

4. 获得所有文章；这样在以后，你会发现 `_posts` 仓库保存了所有的文件；你只需执行一条命令
``` bash
$ git clone git@github.com:yourname/_posts.git
```
所有的博文都会下载到本地,以后只需要配置环境了，方便迁移。
