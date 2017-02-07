---
layout: post
title: 如何利用FTBUtilities创建指导手册
tags: [wiki]
description: >
  对原作者[wiki](http://guides.latmod.com/)的翻译
---

可以查看[LatBlocks](https://github.com/LatvianModder/LatBlocks/tree/1.9/src/main/resources/assets/latblocks/guide)作为参考。
手册是用树状的json数据写成的，请注意编码一定要是UTF-8。

### 结构
手册是从`assets/resourcepacks`这个位置加载的，每一个手册都有自己的一个ID，手册之间能够相互覆盖（就有点像材质的覆盖）。如果你想在整合包中添加手册，还是推荐使用`ResourceLoader`这个模组。

首先，你要在`assets/id/guide`目录下创建json文件，json文件中需要包含：

* `"name":"这是一个你想添加的名字"`
* `"type":"mod"/"modpack"/"other"` —— 手册的类型，方便分类浏览。
* `"authors":["第一作者姓名", "第二作者姓名"]` —— 这个模组或者整合包的作者列表。如果你想要添加手册的作者姓名，看下一条。
* `"guide_authors":[巴拉巴拉]` —— 随便写，如果不写，将会从作者条目自动调用。
* `"icon": "id:textures/logo_guide.png"` —— 图标的材质位置。

### 书写格式
书写也支持Minecraft的`§`字符来定义字体颜色和格式。
比如：

         §4 - 暗红色
         §l - 加粗

但是不推荐这个用法，完全可以用`"text"`来达到相同效果。
关于更多的书写格式，可以看Minecraft的[wiki](http://minecraft.gamepedia.com/Formatting_codes)。

### 自定义链接
如果你想添加图片，特殊文字，悬浮文字或者点击的事件，你需要把相关东西写入到`{`和`}`里面。不支持多个链接。
你可以查看Minecraft的[wiki](http://minecraft.gamepedia.com/Commands#tellraw)查看更多关于tellraw指令的用法。
这里也有一个[工具](https://www.minecraftjson.com/)可以可视化创建tellraw指令

### 应用举例

```json
"Hello"
{"text":"Hello", "color":"red", "bold":true}
{"text":"Some text", "hover":"Line 1"}
```
图片被存储在`modpack/images/`下面，服务器不支持这种非连接形式图片。

```json
{"image":"some_recipe.png"}
{"image":"some_recipe.png", "scale":-3}
{"image":"some_logo.png", "width":250, "height":150}
{"image":"http://i.imgur.com/VyxIO5u.png", "isURL":true}
```
你可以用这些字符作为点击类型：`"cmd", "show_cmd", "url", "file"`

```json
{"text":"Teleport to spawn", "click":{"type":"cmd", "data":"spawn"}}
```

### 未来打算添加的特性
```json
{"recipe":"minecraft:stone", "default_page":0} // NEI and JEI support
```
