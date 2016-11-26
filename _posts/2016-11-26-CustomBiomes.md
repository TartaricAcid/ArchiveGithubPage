## 开始
原作者的wiki：[戳我](https://github.com/Glitchfiend/BiomesOPlenty/wiki/Configuring-Biomes)

### 请注意
在使用自定义生物群系之前，你可能需要：

1. 有使用Forge的经验

1. 了解JSON语法
   > 补充：网上随便搜索的一篇教程：[戳我](http://www.w3school.com.cn/json/)

1. 能够知道哪些选项是可以用的，哪些不可以用

自定义生物群系的自由度可能不及你想象的那么高，但是对于那些不怎么懂编程，但是又希望做一些小变化的人群来说是非常适合的

你所要做的就是去`config/biomesoplenty/`目录下面找到生物群系的配置文件夹，创建一个配置文件，使用正确的语法去自定义自己想要的特性

这看起来很麻烦，但是实际是很简单的一件事情。

顺便提醒一下，配置文件的放置位置是十分重要的，如果放置位置不对，系统会默认生成一个配置文件。

首先，我们需要创建一个以 .json 为拓展名的文件，这个文件必须放在 `/config/biomesoplenty/biomes/`文件夹下面


配置文件的名字是生物群系名称的小写，空格用下划线来表示

举个例子：
一个改变"Origin Valley"生物群系的配置文件的正确命名是 origin_valley.json

我们可以在 `/config/biomesoplenty/`文件夹下面的`biome_ids.json`文件中找到超多生物群系mod的所有生物群系的名称

需要注意的是，在读取配置文件时候出现的任何一个微小的错误都将导致启动失败

GSON（一个专门负责读取配置文件的工具）会提供错误源信息

> **补充：我这里也推荐一个中文网站：[kjson](http://www.kjson.com/)，可以校验json有没有语法错误**

## 基本数据结构
所有的生物群系都有一组通用的配置属性，我们必须需要特定的属性名称才能修改这些属性

下面是一个列表列出了所有的属性名称

| 数据类型 | 属性名称 | 备注 |
|  --- |      ---      |     ---     |
| String | `biomeName` | 生物群系的名称 会在F3的调试窗口中显示 例如"Origin Valley" |
| Block State | `topBlock` | 生物群系表层的方块 比如 Grass |
| Block State | `fillerBlock` | 接近地表的方块 比如 Dirt |
| Block State | `seaFloorBlock` | 在生物群系中湖泊水底的方块，比如 Mud |
| Float | `rootHeight` | 这个生物群系基线的高度 数值在-2.0到2.0之间 |
| Float | `variation` | 生物群系竖直方向高度偏差 数值在0.0到1.0之间 |
| Float | `temperature` | 生物群系的温度 数值在-0.5到2.0之间 |
| Float | `rainfall` | 生物群系的湿度 数值在0.0到1.0之间 |
| Integer | `color` | 在地图上该生物群系的颜色 用十进制数值表示 |
| Integer | `waterColorMultiplier` | 该生物群系水体的颜色 用十进制数值表示 |
| Boolean | `enableRain` | 该生物群系是否能下雨 |
| Boolean | `enableSnow` | 该生物群系是否能下雪 |
| Integer | `skyColor` | 该生物群系天空的颜色 用十进制数值表示 |
| Boolean | `hasBiomeEssence` | 在该生物群系使用生物群系雷达 是否会掉落生物群系精华 |
| Boolean | `canSpawnInBiome` | 玩家是否能出生在该生物群系  |
| Boolean | `canGenerateVillages` | 是否能生成村庄 |
| Boolean | `canGenerateRivers` | 是否能生成河流 |
| Integer | `beachBiomeId` | 毗邻这个生物群系的沙滩生物群系的id 设为-1禁止沙滩的生成  |
| Weight |  `weights` | 生物群系的权重 |
| Object | `generators` | 生物群系生成的植被等 比如 flowers, trees, grasses 等 |
| Array | `entities` | 所有可以生成在该生物群系的实体生物 包括它们的生成权重 一次生成的最小和最大数量 |

## 方块的数据格式
使用下列语句

    {
        "block": "<domain>:<block_id>",
        "properties":
         {
            "property1": "value1",
            "property2": "value2"
         }
    }

## 生成权重数据格式
接下来是一个生成权重的数据格式，实际上并不需要这么多，举这么个例子只是为了列出所有的生物群系

    {
        "ice_cap": 5,
        "tundra": 2,
        "boreal": 7,
        "cold_swamp": 3,
        "wet_temperate": 5,
        "dry_temperate": 10,
        "cool_temperate": 9,
        "warm_temperate": 4,
        "hot_swamp": 4,
        "tropical": 8,
        "ice_cap": 8,
        "mediteranean": 6,
        "savanna": 6,
        "hot_desert": 7,
        "wasteland": 1,
    }

## 实体生成的数据格式
接下来这个例子是关于实体生成的

实体的名称是不区分大小写，不包含空格和下划线的，一个“.”作为mod的分隔符（举个列子：`biomesoplenty.wasp`），可以添加/修改生成不同的实体生物。

对于`creatureType`条目，依据所生成实体生物的类型选择`MONSTER`，`CREATURE`，`AMBIENT` 和 `WATER_CREATURE`。

    [
        {
            "name": "biomesoplenty.wasp",
            "creatureType": "MONSTER",
            "weight": 5,
            "minGroupCount": 50,
            "maxGroupCount": 100
        },
        {
            "name": "sheep",
            "creatureType": "CREATURE",
            "weight": 5,
            "minGroupCount": 2,
            "maxGroupCount": 5
        },
        {
            "name": "squid",
            "creatureType": "WATER_CREATURE",
            "weight": 5,
            "minGroupCount": 8,
            "maxGroupCount": 10
        }
    ]
