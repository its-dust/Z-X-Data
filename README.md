# Z/X 数据 说明文档

## · 请求的数据内容

1. 卡牌信息
2. 卡牌图片
3. 其他图片

| 类型     | 文件格式 |
| -------- | -------- |
| 卡牌信息 | json     |
| 卡牌图片 | png、jpg |
| 其他图片 | png、jpg |

**数据编码格式** `UTF-8`

**卡牌信息可以一张一个`json`文件保存**

文件命名方式`{id}.json` 示例 `E30-007-R.json`

**也可以放于同一个`json`文件里，但需要在前面加上`id`**

```json
{
	"E30-007-R":{
		...
	},
	"E14-001-R":{
		...
	},
	...
}
```



## · 卡牌信息

###### 注：没有内容的请用 - 代替，以确保数据准确性

| 名称        | 数据类型    | 内容          | 示例                    | 备注                                                         |
| ----------- | ----------- | ------------- | ----------------------- | ------------------------------------------------------------ |
| cid         | string      | 卡牌编号      | E30-007                 | 必须*（统一用大写）                                          |
| rarity      | string      | 卡牌罕度      | R                       | 必须*（统一用大写）隐藏版请后跟`-secret`                     |
| zh          | string      | 卡牌名称-中文 | 混祸无限祈装 荆原       |                                                              |
| jp          | string      | 卡牌名称-日文 | 混禍の無限祈装 バラハラ |                                                              |
| ot          | string      | 卡牌名称-俗名 | -                       |                                                              |
| color       | string      | 卡牌颜色      | 黑                      | 无、红、绿、蓝、白、黑（统一使用中文）                       |
| group       | string      | 种族          | 无限助燃/残酷龙         |                                                              |
| card-bag    | string      | 所属卡包      | E30「偶巫女！」         |                                                              |
| type        | string      | 卡牌类型      | Z/X TOKEN               | Z/X、Z/B EX、Z/B OB、Z/X TOKEN、事件、事件 EX、剑临、玩家、玩家 EX、标记（统一用大写，复合类型中间用空格） |
| cost        | string      | 费用          | <~>                     | `∞` 以 `<~>` 代替                                            |
| power       | int         | 力量          | 10500                   | 这一项没有内容的话请置空，不要用`-`代替                      |
| sign        | string      | 标记          | -                       | 点燃、觉醒之种                                               |
| ability     | 数组/string | 能力          | [“ab-1”,”ad-2”]         | 无内容请使用`[]`，不要用`-`代替                              |
| illustrator | string      | 插画师        | 吟                      |                                                              |
| lines       | string      | 台词          | 崇高なる死はあるのか…   |                                                              |
| id          | string      | 编号-罕度     | E30-007-R               | 必须*（统一用大写）用于校验                                  |

### · 模板

```json
{
    "cid":"{编号}",
    "rarity":"{罕度}",
    "name":{
        "zh":"{中文名}",
        "jp":"{日文名}",
        "ot":"{俗名}"
    },
    "attribute":{
        "color":"{颜色}",
        "group":"{种族}",
        "card-bag":"{卡包}"
    },
    "info":{
        "type":"{卡牌类型}",
        "cost":"{费用}",
        "power":"{力量}",
        "sign":"{标记}",
        "ability":["{能力1}","{能力2}","..."]
    },
    "other":{
        "illustrator":"{绘师}",
        "lines":"{台词}"
    },
    "id":"{编号}-{罕度}"
}
```

###  · DEMO

[E30-007 R](http://zxcard.yimieji.com/Cards/E30/E30-007/R)

```json
{
    "cid":"E30-007",
    "rarity":"R",
    "name":{
        "zh":"混祸无限祈装 荆原",
        "jp":"混禍の無限祈装 バラハラ",
        "ot":"-"
    },
    "attribute":{
        "color":"黑",
        "group":"无限助燃/残酷龙",
        "card-bag":"E30「偶巫女！」"
    },
    "info":{
        "type":"Z/X TOKEN",
        "cost":"<~>",
        "power":"10500",
        "sign":"-",
        "ability":["【自】【有效】《自己回合》方阵【诱发条件】这张卡登场。【效果】将你卡组最上方的最多4张卡放置到废弃区。你的废弃区中的卡有13张以上的场合，选择通常方阵上的最多1张Z/X，将其破坏。有20张以上的场合，将这张卡破坏，选择你废弃区中的1张卡名含有「王国屠灭者」的Z/X，以重启状态登场到没有Z/X存在的通常方阵上。","【自】【有效】通常方阵【诱发条件】回合结束时。【效果】方阵上没有你的处于超越状态的Z/X的场合，将这张卡破坏。"]
    },
    "other":{
        "illustrator":"吟",
        "lines":"崇高なる死はあるのか。絶望は紡がれるのか。和を結ぶだと？　心底虫酸が走る。……貴様の薄っぺらい笑いにもだ、バラハラ。　～レルムレイザー～"
    },
    "id":"E30-007-R"
}
```

[E22-069 R（隐藏）](http://zxcard.yimieji.com/Cards/E22/E22-069/R-secret)

```json
{
    "cid":"E22-069",
    "rarity":"R-secret",
    "name":{
        "zh":"旋律",
        "jp":"メロディ",
        "ot":"红偶像KEY"
    },
    "attribute":{
        "color":"无",
        "group":"-",
        "card-bag":"E22「幻梦舞台！！」"
    },
    "info":{
        "type":"标记",
        "cost":"-",
        "power":"",
        "sign":"-",
        "ability":[]
    },
    "other":{
        "illustrator":"-",
        "lines":"-"
    },
    "id":"E22-069-R-secret"
}
```

[E33-022 R](http://zxcard.yimieji.com/Cards/E33/E33-022/R)

```json
{
    "cid":"E33-022",
    "rarity":"R",
    "name":{
        "zh":"卡娜 投票券",
        "jp":"カナ投票券",
        "ot":"-"
    },
    "attribute":{
        "color":"无",
        "group":"-",
        "card-bag":"E33「偶像♪夏日课程」"
    },
    "info":{
        "type":"标记",
        "cost":"-",
        "power":"",
        "sign":"-",
        "ability":[]
    },
    "other":{
        "illustrator":"yaki*mayu",
        "lines":"-"
    },
    "id":"E33-022-R"
}
```



## · 图片

*Z/X、Z/B EX、Z/B OB、Z/X TOKEN、事件、事件 EX、剑临、玩家、玩家 EX、标记等卡图*

*卡背图片、颜色图标、标记图标、场地图*

- 带有透明背景的图片（卡图、标记、颜色）使用`png`格式
- 一般（场地，宣传）可以用`jpg`

![混禍の無限祈装 バラハラ](http://zximg-cdn.yimieji.com/card/E30/E30-007.png)![メロディ](http://zximg-cdn.yimieji.com/card/E22/E22-069.png)![カナ投票券](http://zximg-cdn.yimieji.com/card/E33/E33-022.png)

![ig](http://zxcard.yimieji.com/themes/zx_icon/mark_IG.jpg)![ig](http://zxcard.yimieji.com/themes/zx_icon/mark_ES.jpg)![red](https://www.zxtcg.com/common/icon_img/w_red_sp.png)![blue](https://www.zxtcg.com/common/icon_img/w_blue_sp.png)![white](https://www.zxtcg.com/common/icon_img/w_white_sp.png)![black](https://www.zxtcg.com/common/icon_img/w_black_sp.png)![green](https://www.zxtcg.com/common/icon_img/w_green_sp.png)![null](https://www.zxtcg.com/common/icon_img/w_mu_sp.png)![sleep](https://www.zxtcg.com/rule/image/icon_sleep.png)

![field](https://www.zxtcg.com/rule/image/manual_field.png)