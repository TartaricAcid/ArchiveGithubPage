---
layout: post
title: Deep Resonance 教程文案
tags: [wiki]
description: >
  The One Probe 是由McJty制作的一个以特殊方式产生RF能量的模组
---

# Deep Resonance （深度共振）
Deep Resonance （以下皆简称为DR）独创了一种特殊的产生RF能源方式，即创新性的创造了一种叫做共振水晶的方块来产生RF能量。整个模组主要就是围绕如何得到共振水晶和提升共振水晶质量两方面进行。鼓励玩家利用设计好的方块实现共振水晶自动化。相比于其他模组的无脑发电方式更具有游戏性。

该模组是开源的，可以在原作者的[GitHub](https://github.com/McJty/DeepResonance)页面找到这个模组的源码。

该模组提供的方块并不多，多是与水晶自动化有关的机器。
![DR一览表](https://github.com/TartaricAcid/tartaricacid.github.io/blob/master/public/img/DeepResonance/001.PNG?raw=true)

该模组提供了详细的说明手册，但是由于McJty的一贯个性，并没有本地化可以用。所以这里给出手册的翻译，以及我对手册讲解的补充或者无用部分的删减（是的，删减很多。作者写了很多趣味性的话，但是这是mod教程，我就省去了。嗯，就是这样）。由于英语水平以及个人能力的有限，有错误还请诸位多多指正和见谅。

---
## 1. 共振矿石
开启这个模组冒险之旅最起始的东西，这个模组许多合成需要它做原料。当然更多时候是用来熔化制作共振水晶的。  
默认在`2-30`的高度生成，默认尝试生成`3`次，默认生成`5-8`个。  
这些都可以在配置文件中更改生成，这里给出截取的配置文件部分，这部分配置文件位于`config\deepresonance\main.cfg`下面`471-504`行。

```javascript
# Chances for the ore to spawn in a chunk
# 一个区块尝试生成矿物的次数。
I:chancesToSpawn=3

# Maximum size of the ore veines
# 矿脉最大生成个数。
I:maxVeinSize=8

# Maximum ore height
# 矿石最大生成高度。
I:maxY=30

# Minimum size of the ore veines
# 矿脉最小生成个数。
I:minVeinSize=5

# Minimum ore height
# 矿石最小生成高度。
I:minY=2

# Enable this if you want to get retrogen (generation of ores/crystals) for already existing chunks
# 是否想要重新生成（在已经存在的区块上面生成矿石/共振水晶）。
B:retrogen=true

```
矿物采掘等级为钻石等级（也就是需要铁镐才能采集），采集掉落原矿。

## 2. 共振水晶
有非常小的几率在矿洞里面发现。天然发现的水晶的属性都不是很好，纯度`(purity)`属性不高，而且发电量很小。  
这里作者有个相对比较奇怪的算法，我就不解释了。大家有兴趣的自己去看吧，我把链接放这里了：[点我](https://github.com/McJty/DeepResonance/blob/master/src/main/java/mcjty/deepresonance/worldgen/DeepWorldGenerator.java)。

需要注意一点，共振水晶附近如果发生爆炸（比如苦力怕的爆炸），那么共振水晶也会受影响发生剧烈爆炸。爆炸的剧烈程度和水晶的强度`(strength)`属性有关系。  

相关配置文件，这部分配置文件位于`config\deepresonance\main.cfg`下面`471-504`行

```javascript
# The chance that a crystal will spawn in a chunk. Higher number means less chance. 0 means no crystal will ever spawn.
# 一个区块生成水晶的几率。数值越大意味生成几率越低。数值设为0说明没有水晶生成。
I:crystalSpawnChance=15

# The number of times that the worldgen will try to spawn a crystal in a chunk before it fails.
# 一个区块尝试生成水晶的次数。
I:crystalSpawnTries=10

# Enable this if you want to see in the log where crystals are spawned
# 打开这个，就可以在日志中看见水晶生成的信息。
B:verboseSpawn=false
```
## 水晶属性说明
每个水晶有四个属性

* Strength（强度）：强度标定着一个水晶能产生的能量的多少。一般数值都在0%-100%之间，当然，还可能出现`OverCharge`的水晶，它可以产生更多的电量（也意味着更危险）。
* Efficiency（效率）：效率标定着一个水晶产生能量的速率，效率越高意味着产生能量的速率越快。
* Purity（纯度）：纯度表定着一个水晶发电时候辐射程度，纯度越低，发电时候产生的辐射就越厉害，同时发电量速率也会更低。
* Power（能量）：能量数值说明了当前水晶中存储的能量的多少，反映了水晶能量产出的最大量。
