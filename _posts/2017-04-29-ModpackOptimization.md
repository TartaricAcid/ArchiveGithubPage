---
layout: post
title: 1.10.2整合包优化详解
tags: [essay]
description: >
  是对之前那篇文章的拓展延伸
---

原版1.10.2以其Mojang高超的“优化”，一直被众多玩家所吐槽，但是从开发者角度来说，这些是大有裨益的，关于这些我在上一个帖子中已经说过了，这里不再累述。本篇文章只是单纯叙述如何优化整合包来提升游戏体验。


1. Forge
  * 建议安装最新版forge（我使用的是2221版本的）；
  * 找到config文件夹下的forge.cfg，找到这一段，将false改为true（适用于多核CPU）；
  ``` javascript
  # Enable forge to queue all chunk updates to the Chunk Update thread. May increase FPS significantly, but may also cause weird rendering lag. Not recommended for computers without a significant number of cores available.
  B:alwaysSetupTerrainOffThread=false
  ```
  * 如果游戏中遇到所谓的“幽灵区块加载”导致的延迟（即每隔大约30秒会出现一阵延迟），可以试试修改config文件夹下forgeChunkLoading.cfg这一段的数值。
  ``` javascript
  # Unloaded chunks can first be kept in a dormant cache for quicker
  # loading times. Specify the size (in chunks) of that cache here
  I:dormantChunkCacheSize=0
  ```
2. FoamFix
  * 下载地址在这里找：[戳我啊](http://www.asie.pl/Projects/Minecraft/Mods/FoamFix/)；
  * 任意选择两个版本中一个即可，对于玩家没有区别；
  * 能够有效减少内存使用大约一半左右。

3. BetterFPS
  * BetterFPS采用了优化的渲染算法，恰好和FoamFix形成优势互补；
  * 在游戏中默认按下F12可以打开BetterFPS的渲染算法选项，可以试试调换几种算法，重启后生效。

4. Optifine
  * Optifine可能会和一些模组有冲突，不过目前来看并不多，问题不大；
  * Optifine的快速渲染选项往往有奇效，比如能够解决`The Betweenlands`模组导致的FPS骤降问题；
  * Optifine能够关闭所有的动画和粒子效果，这个也对FPS提升有效果；
  * 经过测试发现，关闭迷雾能够有效提升FPS；
  * Optifine还有多核心加载，稳定帧率等方法可用，游戏中均有详细说明，此处不再累述。

5. Surge
  * 能够关闭一些材质动画效果，可能对老旧CPU优化性能较好；
  * 但是这个模组兼容性很差，已经发现比较多的模组冲突问题。

6. 其他
  * 调节原版自带的Mipmap可能会有效果；
  * Mipmap的作用能够使远处画面看起来平滑，所以远处树叶草地有时候出现的材质问题可能是Mipmap等级太低导致的。
