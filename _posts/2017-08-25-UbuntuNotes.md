---
layout: post
title: 使用一段时间Ubuntu系统后的小结
tags: [essay]
description: >
  我并不是计算机专业学生，对计算机只是出于爱好。很多东西都带有许多主观感想在里面，还请多多谅解。
---

首先先说下我目前电脑系统的相关信息：

> 操作系统：window 7 旗舰版 和 Ubuntu 16.04 LTS 双系统
>
> 内存：11.6 GB
>
> CPU：Intel® Core™ i3-2370M CPU @ 2.40GHz × 4 
>
> 显卡：Intel® Sandybridge Mobile 和 NVIDIA GEFORCE 720M

# 1. 为什么我要用Ubuntu

起因很简单，我想学习下linux系统。先前我的舍友在我电脑上装过一个Ubuntu Kylin系统。不过由于kylin的问题，还有我对linux系统的不熟悉，这个系统除了白白耗去我100G的硬盘空间外别无用处。最近又突发奇想，想来捣鼓捣鼓linux系统，于是把原来的Kylin卸载了，换成了Ubuntu 16.04 LTS系统。

谈到这里，估计很多读者应该马上就会说到：Debian大法好，Arch大法好之类的话。不过我是初学者，而且学习linux系统的目的也仅仅是能够跑日常的工作环境，写写java，跑跑前端，做做Minecraft的本地化。Ubuntu用户量大，而且操作方便，兼容的软件多，确实是不二的选择。

Ubuntu的安装网络上教程恐怕已经铺天盖地了，我就不再多说了。一般常用的是做一个U盘的启动盘安装系统，不过我的U盘上面有很多有用的东西，我也没有地方暂存它。我电脑自带一个光驱，所以特意跑去电脑店花了5块钱买了个空白DVD盘，刻了一个启动光盘安装，倒也是轻松快捷。

话不多说，展示下我现在的桌面（我装了Mac相关的主题，所以大家不要惊讶。桌面是射命丸文哦）

![Imgur](http://i.imgur.com/CTYpiDk.png)

# 2. 我的Ubuntu装了什么

分成各个功能来讲吧

## 1. 驱动


Ubuntu自带的驱动都没啥问题，唯独就是这个NVIDIA的显卡驱动，我前后折腾了三四天。期间还曾经把grub引导整坏了一次。要么就是开机无限循环登录，要么就是Minecraft运行崩溃。就在我几乎绝望的时候，我打开了系统设置中的软件与更新。看到了这个……![image](https://public.lightpic.info/image/B882_599FE9D80.jpg)

当时我的心情是绝望的，Ubuntu居然自带一个NVIDIA的显卡驱动。于是我果断切换驱动，重启，打开Minecraft。完美运行不崩溃，这才是我要的！

调节了几个配置以后，果然，这直播的顺畅感简直顺滑无比，60fps几乎不带跌的，这还是直播啊，瞬间感觉——这么折腾值了！

其次是声卡驱动，反正我的耳麦插上去就是没法识别设备，百度也查不到相关资料。反正就是没法录音……

其他的驱动目前没发现任何问题。

## 2. 基本软件

基本软件？文档的话自带的LibreOffice套件已经足够用了，如果不喜欢也可以去换WPS，反正也有linux版的。都和office兼容，问题不大。

音乐播放，视频播放自带的软件几乎没有什么问题。不过一般看视频都用手机吧，听音乐用网易云就行，还挺好使，音量设置界面直接就能打开网易云，这一块真心是做的好。

![003](https://public.lightpic.info/image/0A71_599FED020.jpg)

文本编辑这一块自带的gedit还挺不错，不过我可是Atom用户，怎么能抛弃？Ubuntu下的Atom和Windows下的atom一模一样，连插件都是通用的，非常顺手。顺带还装了个Sublime，Sublime处理小文件挺快捷的，反正我是不太想用gedit。据说微软爸爸的vsc也有linux版本。

图为Ubuntu下的Sublime和Atom。

![004](https://public.lightpic.info/image/1807_599FEEB30.jpg)

浏览器当然是我们的谷歌浏览器啦~\(≧▽≦)/~，虽然Ubuntu自带一个火狐浏览器，不过那个火狐浏览器是英文界面。而且我曾经是火狐用户，每次点开火狐，那卡卡的启动，那不厌其烦的更新提示，能把人气死。其次我喜欢谷歌的一个叫infinity插件，美观好用。（不知道火狐底下有没有类似的插件）

![005](https://public.lightpic.info/image/9957_599FF04D0.jpg)

Markdown编写器我用的是Typora，这个也有Windows版本。虽然一开始看起来其貌不扬，但是用了以后觉得：真™好用啊，不但支持数学公式，流程图的插入，还有快捷键快速插入语法的功能：

> Shift + Ctrl + I：快速插入图片
>
> Shift + Ctrl + `：快速插入代码块

只举了几个简单的例子。插入表格功能的便捷程度我已经无语了，当初用Atom写大片大片的表格简直能够把人写哭了。

输入法，额……搜狗就够了，Ubuntu自带的那个在联想输入方面还是比较差的。

即时语音文字通信软件？QQ？别想了，腾讯官方一定是觉得linux用户很穷，只有一个远古版本的QQ，而且这货现在不能用了！至于那些用 wine+QQ 的法子我也试过了，都不能用。一句话——我选discord。

对了，如果想要通过手机发送QQ消息的话，一定需要个文件传输软件吧，我现在用的Send Anywhere，还挺方便的，重要的东西通过这个发送到手机，然后手机转发到QQ还算不错。

![006](https://public.lightpic.info/image/67F8_599FF2CA0.jpg)

截屏软件？Ubuntu自带的很好用。

录屏软件？用obs呀，直播+录制双合一。而且总觉得这货好像比Windows下的颜值高了不少？一定是我的错觉。

![007](https://public.lightpic.info/image/DBD2_599FF4990.jpg)

软件安装？什么，linux系统你还要什么软件安装工具？！一个终端就解决了啊……

额……还是有些软件需要自己手动安装的，我用了个别人推荐的GDebi软件，用它打开`.deb`文件就行，能够自动的把缺的前置补全。别去用Ubuntu自带的软件中心，十分辣鸡！

远程桌面？ssh就行了啊。不过要有那种类似于图像化的界面，我还是推荐 rdesktop。（图为用rdesktop连接一个 Windows Sever 2012 的服务器）

![009](https://public.lightpic.info/image/C1CB_599FFAA50.jpg)



FTP？一堆工具可选，自个儿百度吧。

图像编辑，刚刚处理图像用了下gimp，还真别说，就和Photoshop一样的手感，挺好用的。不过要记得调节成“单窗口模式”，不然浮动的窗口模式我是接受不了。给大家看看截图：

![010](https://public.lightpic.info/image/9987_599FFBAB0.jpg)

至于视频，音频之类的软件我试过几个网上推荐的，但都不太顺手。连3D建模的动画制作软件都有的。要是真搞这些，还是老老实实用adobe家族的软件吧。



## 3. 开发工具

linux系统相比于Windows的优势就在于此，搞开发十分方便。Ubuntu 16.04 LTS 本身自带 Python，Open JDK这两个库。Open JDK本身也比较新，不过别人都还是推荐用Oracle JDK。通过`apt-get`指令安装库也十分方便。当初想在Windows下跑jekyll，折腾ruby就折腾了一天，到最后也没弄好。在Ubuntu下三条指令一打，三分钟不到就完事了。

集成开发环境也都齐全，我平时也就学学java，所以装了个Eclipse（IDEA党退散），还是熟悉的界面，还是熟悉的味道。

![011](https://public.lightpic.info/image/6941_599FFEDD0.jpg)

git？额，git还要啥客户端，终端就是你的家。不过我不是用Atom用户么，Atom本身自带一个git客户端，还能吧东西推送到github。

前端？Atom又笑嘻嘻的站了出来，装上emmet插件以及其他辅助插件，打开你的谷歌浏览器。应该也就没啥别的IDE啥事了。

## 4. 游戏

大哥，好好工作，别玩游戏！

好吧，跑跑Minecraft还是没问题的，毕竟Minecraft是用Java写的。

> Java：一处编译，处处运(bào)行(zhà)

启动器用官方启动器就行，或者你用HMCL也行。不过我还是推荐MuiltMC。

![012](https://public.lightpic.info/image/CEB7_59A001BC0.jpg)

至于其他游戏么……与其折腾在linux上，你还是切Windows系统吧，我感觉这东西瞎折腾没有意义。

啊，差点忘了说了，国际知名理财软件Sbteam现已登录Ubuntu，欲购从速啊。