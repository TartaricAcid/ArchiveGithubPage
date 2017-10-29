---
layout: post
title: 基于Mkdocs和ReadTheDocs的文档网站的构建
tags: [wiki]
description: >
  学习心得，记录一下
---
事情发生的原因也实属偶然，昨天再看`Sponge`的教程时候，偶然间看到了它的文档网站制作精良，界面好看。又突然想起我前几天折腾太玄的lua教程文档时候的繁琐程度，加之不喜欢gitbook和github wiki的界面。于是决定尝试去好好研究下这个网站用的是什么框架构架的。

最后研究出结论：
* 网站是用`Read the Docs`网站自动构建的，能够直接加载github仓库的文件自动生成文档页面；
* 文档是采用一种叫做`reStructuredText`的语言书写的，这种语言和`markdown`颇为相似。
* `Read the Docs`网站除了能够自动构建`reStructuredText`语言，还支持`markdown`语言的构建。
* 处理`reStructuredText`语言所用的构建框架是`Sphinx`，这本来是Python官方用来构建文档的工具，不过随后就发展成为了一个大众可用的框架。
* 处理`markdown`语言所使用的构建框架是`Mkdocs`，能够将其自动处理成好看的文档。不过功能上要比`reStructuredText`语言稍差。

能够免费构建markdown语法书写的文档？！这一下就打动了我，研究一番后写出这面简单的心得，分享给大家。

相关链接：
* [Mkdocs官网](http://www.mkdocs.org/)
* [Mkdocs中文文档](http://markdown-docs-zh.readthedocs.io/zh_CN/latest/)
* [ReadTheDocs官网](https://readthedocs.org/)
* [ReadTheDocs官方文档](https://docs.readthedocs.io/en/latest/index.html)

## 1.Mkdocs环境的构建
实际上，如果你的电脑操作系统是Windows的话，不推荐你了解这一部分。Windows下开发环境的构建一直为人所诟病，而且这个环境的搭建仅仅是方便实时调试用，只需要写好一个yml配置文件，导入ReadTheDocs网站，该网站会自动构建文档网页。所以费时费力去折腾环境搭建违背了本篇教程的本意。

但是你的电脑是Linux系统就另当别论了，只需要如下指令即可安装Mkdocs：

```
$ pip install mkdocs
```

需要注意这个框架是用Python写的，请务必保证你的Python的安装。

之后的常用指令只有这几个：

| 指令         | 用途                  |
| :----------: | :------------------: |
| `mkdocs new` | 构建一个新的mkdocs工程 |
| `mkdocs serve` | 在本机构建出调试用的文档网页 |
| `mkdocs build` | 在本机构建出实际可用的文档网页 |
| `mkdocs gh-deploy` | 将你写的文档部署到github page |

当我们构建了新的工程之后，工程结构也很简单，基本上是如下样子

```
.
├── docs
│   └── index.md
└── mkdocs.yml
```

`mkdocs.yml`文件是配置文件，到时候`ReadTheDocs`自动构建时候，也是是别的文件主目录下的这个配置文件。

`docs`文件夹是放置文档的地方，里面的`index.md`就是文件的索引了。

## 2.配置文件的书写
官方文档讲了一堆堆配置文件，我只挑一些重要的来说下，有一个`pages`相关配置死活有问题。

```yml
site_name: Mkdocs教程
theme: readthedocs
repo_url: https://github.com/TartaricAcid/Mkdocs
site_favicon: favicon.ico
copyright: 酒石酸的测试项目
```

来解释下每个配置啥意思，除了`site_name`是必须要有的，其他的都可选。
* site_name：必须的一条，设定网页的名字；
* theme：网页主题，默认的不好看，推荐`readthedocs`；
* repo_url：文档相关仓库地址，可以再网页上面生成一个github跳转链接；
* site_favicon：网站的图标，需要将`favicon.ico`放置在`docs`文件夹下；
* copyright：版权声明。会在网页最下面版权处显示你所写的东西。

然后随意在你的docs文件夹下放置markdown文件吧，框架会很智能的将这个文件夹下所有的`md`文件均加载上去，并按照文件夹的排列整齐划一的排布，完全不用操心别的。

```
docs
   ├── about.md
   ├── index.md
   ├── 第一章
   │   ├── 第一节-如何开始.md
   │   └── 第二节-明白了吗.md
   └── 第二章
       ├── 第一节-这是什么.md
       ├── 第二节-咋开始啊.md
       └── 第三节-这么回事.md
```

> 除了`index.md`和`about.md`命名是有限制的，其他都很随意。

## 3.使用ReadTheDocs自动构建文档网页
ReadTheDocs网站是免费网站，能够自动抓取github制定仓库的文件，自动构建出可以观看的网页，并且还主动给你分配一个域名来访问这个文档页面。

首先，申请一个ReadTheDocs账户，并将其与你的github账户连接。
![pic](https://public.lightpic.info/image/E069_59F5D07C0.jpg)

然后导入你的仓库
![pic](https://public.lightpic.info/image/8407_59F5D07C0.jpg)

然后进入你的工程界面，就是这个样子啦
![pic](https://public.lightpic.info/image/6B43_59F5D07C0.jpg)
可以在右侧看到构建情况，以及自动分配的域名。

不过默认是用的`Sphinx`构建网页，我们得先调节一下配置，点击图中的`Admin`按钮，找到setting部分
![pic](https://public.lightpic.info/image/65FC_59F5D07C0.jpg)

往下翻，调节这一处的`Documention type`即可（你还可以顺手调节下语言）
![pic](https://public.lightpic.info/image/1D07_59F5D07B0.jpg)

然后在工程主页找到给你的域名就能访问文档了，欢呼吧
![pic](https://public.lightpic.info/image/A98B_59F5D3170.jpg)

不过，有一件事需要注意，Mkdocs识别的markdown和我们github用的markdown有些不同的，具体咱可以看看这个教程，写的很详细：
[CommonMark官方说明文档](http://commonmark.org/help/)
