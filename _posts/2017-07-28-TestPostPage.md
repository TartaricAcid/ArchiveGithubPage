---
layout: post
title: 发现了个新玩具
tags: [essay]
description: >
  今天乱逛网站，发现一个日本modder用了个API很好，我来测试下
---

很简单的一个API，能够显示GitHub的活跃记录。不过加载会稍慢点。      
这是该项目的GitHub地址：[戳我啊](https://github.com/2016rshah/githubchart-api)    
这是该项目的网站地址（额，我很想吐槽这太简陋了）：[戳我啊](http://ghchart.rshah.org/)

写法很简单，在你的html或者mrakdown文件中插入这一段就行。

```html
<img src="http://ghchart.rshah.org/2016rshah" alt="2016rshah's Github chart" />
```
示例中的`http://ghchart.rshah.org/2016rshah`最后的`2016rshah`可以要换成自己的GitHub的账户名称，注意大小写。比如我的就应该写成`http://ghchart.rshah.org/TartaricAcid`。   
其次是`2016rshah's Github chart`这一段，可以随便填写，填写好后会显示成记录图下方的文字。比如我就写成`Baka943的刷单记录`。

最后给大家看下效果

<img src="http://ghchart.rshah.org/TartaricAcid" alt="Baka943的刷单记录" />
