---
layout: post
title: Actually Computer 函数文档
tags: [wiki]
description: >
  第一个模组就给我来个下马威，原作者也没写外部文档。没关系，源码里面扒出来了。
---

### 堆肥机（Compost）
| 函数 | 说明 |
| :--: | :--: |
|getConversionTime|function():number; 返回当前转化已经消耗的时间，最大为3000|

### 自动饲育机（Feeder）
| 函数 | 说明 |
| :--: | :--: |
|getCurrentTimer|function():number; 返回饲育机投食的冷却时间|
|getAnimalsInRange|function():number; 返回当前饲育机检索动物的数量|

### 幻灵接口（Phantomface）
| 函数 | 说明 |
| :--: | :--: |
|getBoundPosition|function():number,number,number; 返回幻灵接口绑定的方块坐标。|
|getType|function():string; 返回幻灵接口的类型名称|
|setBoundedPosition|function(x:number, y:number, z:number):boolean; 设置坐标绑定方块，如果绑定成功返回true。|

### 经验固化机（XPSolidifier）
| 函数 | 说明 |
| :--: | :--: |
|getXPAmount|function():number; 返回当前存储的经验|

### 微笑云朵（SmileyCloud）
| 函数 | 说明 |
| :--: | :--: |
|getName|function():string; 返回当前微笑云朵的名字|
|setName|function(name:string):boolean; 设置微笑云朵的名字，如果成功返回true。|

### 咖啡制造机（CoffeeMaker）
| 函数 | 说明 |
| :--: | :--: |
|startCoffee|function():boolean; 启动咖啡制造机，如果启动成功则返回true。|

### 其他实用拓展的机器（TileBase）
| 函数 | 说明 |
| :--: | :--: |
|getRedstoneMode|function():string; 返回当前的红石模式|
|setRedstoneMode|function(mode:string):boolean; 设置红石模式；设置成功返回true。|
|isFluidContainer|function():boolean; 如果TileEntity是有流体存储槽则返回true。|
|getTankAmount|function():number; 返回可用的流体存储槽数量。尽可能在操作之前先检查一遍这个！|
|getFluidType|function(tank:number):string; 返回流体存储槽中储存的流体名称|
|getFluidAmount|function(tank:number):number; 返回当前流体槽中流体的存储数量|
|getTankCapacity|function(tank:number):number; 返回流体槽的储存上限|
