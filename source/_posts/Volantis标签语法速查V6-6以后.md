---
title: Volantis标签语法速查V6.6以后
categories: 
  - 博客
  - 语法参考
tags: [主题设置, 标签插件]
sidebar:
  - blogger
  - toc
copyright:
  type: type3
  author: Volantis Team
  ref:
   title: 标签插件
   url: https://volantis.js.org/v6/tag-plugins/
date: 2026-08-08 15:21:49
description:
image:
---

Volantis的标签插件有点多，为了方便书写的时候检索查询，并获得源代码。特提炼转载该参考文档。

> V6 版本采用 `::` 作为参数与内容的分隔符，部分标签使用空格分隔（如 `mark`、`hashtag`）。`[]` 表示可选参数。

<!-- more -->

## 文本符号

### 文本标记

带 {% u 下划线 %} 的文本；带 {% emp 着重号 %} 的文本；带 {% wavy 波浪线 %} 的文本；带 {% del 删除线 %} 的文本

键盘：{% kbd ⌘ %} + {% kbd D %}  密码：{% psw 这里没有验证码 %}

```md
{% u 下划线 %}  {% emp 着重号 %}  {% wavy 波浪线 %}  {% del 删除线 %}
{% kbd ⌘ %} + {% kbd D %}
{% psw 这里没有验证码 %}
```

### mark文本背景色

{% mark 高亮标记 %}  {% mark 自定义颜色 color:red %}

```md
{% mark 高亮标记 %}
{% mark 自定义颜色 color:red %}
```

### hashtag标签

{% hashtag Hexo https://hexo.io %}  {% hashtag Volantis https://volantis.js.org color:blue %}

> 颜色可选：red, orange, yellow, green, cyan, blue, purple（不填则自动轮换）

```md
{% hashtag Hexo https://hexo.io %}
{% hashtag Volantis https://volantis.js.org color:blue %}
```

---

## 文字颜色、段落渲染span

{% span red::红色 %} {% span yellow::黄色 %} {% span green::绿色 %} {% span cyan::青色 %} {% span blue::蓝色 %} {% span gray::灰色 %}

{% span center logo large::GeoNotes %} {% span center small::寓形宇内复几时，曷不委心任去留 %}

`p` 标签用法与 `span` 完全相同，区别是 `p` 渲染为独立段落。

<div style="text-align:center">

| 属性 | 可选值 |
|------|--------|
| 字体 | `logo`, `code` |
| 颜色 | `red`, `yellow`, `green`, `cyan`, `blue`, `gray` |
| 大小 | `small`, `h4`, `h3`, `h2`, `h1`, `large`, `huge`, `ultra` |
| 对齐 | `left`, `center`, `right` |
</div>

```md
{% span red::红色 %} {% span yellow::黄色 %} {% span green::绿色 %}
{% span center logo large::GeoNotes %} {% span center small::寓形宇内复几时，何不委心任去留 %}
```

---

## 备注note

{% note::可以在配置文件中设置默认样式，为简单的一句话提供最简便的写法。 %}

{% note quote::note quote 适合引用一段话 %} {% note info::note info 默认主题色，适合中性的信息 %}

{% note warning::note warning 默认黄色，适合警告性的信息 %} {% note danger::note error/danger 默认红色，适合危险性的信息 %}

{% note success::note done/success 默认绿色，适合正确操作的信息 %}

**更多图标**：

{% note radiation::默认样式 %} {% note radiation yellow::可以加上颜色 %} {% note bug red::说明还存在的一些故障 %}

{% note link green::可以放置一些链接 %} {% note paperclip blue::放置一些附件链接 %} {% note todo::待办事项 %}

> 彩色图标：`quote`, `info`, `warning`, `done/success`, `error/danger`
> 灰色图标（可指定颜色）：`radiation`, `bug`, `idea`, `link`, `paperclip`, `todo`, `message`, `guide`, `download`, `up`, `undo`
> 颜色：`clear`, `light`, `gray`, `red`, `yellow`, `green`, `cyan`, `blue`

```md
{% note::默认样式 %}
{% note quote::引用 %}
{% note info::信息 %}
{% note warning::警告 %}
{% note danger::危险 %}
{% note success::成功 %}

{% note radiation::默认样式 %}
{% note radiation yellow::加上颜色 %}
{% note bug red::故障说明 %}
{% note link green::链接 %}
{% note paperclip blue::附件 %}
{% note todo::待办事项 %}
```

**彩色备注块Note**

{% Note 一共支持12种颜色，可以满足几乎所有的需求了。 color 可设置 red、orange、amber、yellow、green、cyan、blue、purple、light、dark、warning、error 几种取值。 [link](/) %}
{% Note color:cyan 一共支持12种颜色，可以满足几乎所有的需求了。 color 可设置 red、orange、amber、yellow、green、cyan、blue、purple、light、dark、warning、error 几种取值。 [link](/) %}

{% Note 这是标题 这是内容 color:blue %}

```md
{% Note 一共支持12种颜色... color:blue [link](/) %}
{% Note color:cyan 一共支持12种颜色... [link](/) %}
{% Note 标题 内容 color:blue %}
```
---

## noteblock

{% noteblock quote::小标题 %}
Windows 10不是為所有人設計，而是為每個人設計
{% endnoteblock %}

```md
{% noteblock quote::小标题 %}
正文内容...
{% endnoteblock %}

{# 嵌套示例 #}
{% noteblock quote::外层 %}
{% noteblock info::内层 %}
嵌套内容...
{% endnoteblock %}
{% endnoteblock %}
```

---

## 多选框 / 单选框

### 多选框checkbox

{% Checkbox 普通的没有勾选的复选框 %}
{% Checkbox checked:true 普通的已勾选的复选框 %}
{% Checkbox symbol:plus color:green checked:true 显示为加号的绿色的已勾选的复选框 %}
{% Checkbox symbol:minus color:yellow checked:true 显示为减号的黄色的已勾选的复选框 %}
{% Checkbox symbol:times color:red checked:true 显示为乘号的红色的已勾选的复选框 %}

```md
{% Checkbox 普通的没有勾选的复选框 %}
{% Checkbox checked:true 普通的已勾选的复选框 %}
{% Checkbox symbol:plus color:green checked:true 显示为加号的绿色的已勾选的复选框 %}
{% Checkbox symbol:minus color:yellow checked:true 显示为减号的黄色的已勾选的复选框 %}
{% Checkbox symbol:times color:red checked:true 显示为乘号的红色的已勾选的复选框 %}
```

> 参数：`checked: true/false`、`color: red/orange/yellow/green/cyan/blue/purple`、`symbol: plus/minus/times`

### 单选框radio

{% Radio 没有勾选的单选框 %}
{% Radio checked:true 已勾选的单选框 %}

```md
{% Radio 没有勾选的单选框 %}
{% Radio checked:true 已勾选的单选框 %}
```

> 参数：`checked: true/false`、`color: red/orange/yellow/green/cyan/blue/purple`、`symbol: plus/minus/times`

---

## quot引用

### 引用

{% quot 引用内容 %}

{% quot 带图标的引用 icon:default %}

{% quot prefix:bxs:quote-left 带前缀后缀图标 suffix:bxs:quote-right %}

> 参数：`el:h2/h3/p`（元素标签）、`icon:图标名`、`prefix:前缀图标`、`suffix:后缀图标`

```md
{% quot 引用内容 %}
{% quot 带图标的引用 icon:default %}
{% quot prefix:bxs:quote-left 带前缀后缀图标 suffix:bxs:quote-right %}
```
### 段落引用

段落引用，这个是标准写法 > 引用内容 的增强版本，适合不太强调的、大段落的引用。
> 普通引用内容

{% blockquote %}
这是使用 blockquote 标签的例子
{% endblockquote %}

```md
> 普通引用内容

{% blockquote %}
这是使用 blockquote 标签的例子
{% endblockquote %}
```

---

## 时间线

{% Timeline %}
<!-- node 2020-05-15 -->
不需要额外处理。
<!-- node 2020-04-20 -->
1. 全局搜索 `seotitle` 并替换为 `seo_title`。
2. group 组件的索引规则有变。
{% endTimeline %}

> 用 `<!-- node 标题 -->` 注释标记每个时间节点，标题支持 Markdown 链接语法。

```md
{% Timeline %}
<!-- node 2020-05-15 [2.6.3 -> 2.6.6](https://...) -->
不需要额外处理。

<!-- node 2020-04-20 [2.6.2 -> 2.6.3](https://...) -->
1. 全局搜索。
2. group 组件的索引规则有变。
{% endTimeline %}
```

---

## 链接、按钮、卡片

### link

{% link 链接标题::https://example.com::https://example.com/icon.png %}

```md
{% link 链接标题::https://example.com::https://example.com/icon.png %}
```

### button

{% btn 行内按钮:: / %}  {% btn regular::示例博客::https://example.com::fas fa-play-circle %}

> 参数：`regular`, `large`, `center`

```md
{% btn 行内按钮:: / %}
{% btn regular::示例博客::https://example.com::fas fa-play-circle %}
```

### ghcard

{% ghcard 用户信息卡片::用户名 %}

{% ghcard 仓库信息卡片::仓库名 %}

```md
{% ghcard 用户信息卡片::用户名 %} 
{% ghcard 仓库信息卡片::仓库名 %}
```

### site

网站卡片可显示网站截图、logo、标题、描述，需在 `_data/sites.yml` 中配置数据，与友链数据可混用。

### menu

{% menu::下拉菜单示例 %}
{% menuitem 选项一::https://example.com/1 %}
{% menuitem 选项二::https://example.com/2 %}
{% menuitem 选项三::https://example.com/3 %}
{% endmenu %}

```md
{% menu::下拉菜单示例 %}
{% menuitem 选项一::https://example.com/1 %}
{% menuitem 选项二::https://example.com/2 %}
{% menuitem 选项三::https://example.com/3 %}
{% endmenu %}
```

---

## 容器类

### folding

{% folding 查看图片测试 %}
这里的内容会被折叠
{% endfolding %}

{% folding cyan open::默认打开的折叠框 %}
这是一个默认打开的折叠框。
{% endfolding %}

> 颜色：`blue`, `cyan`, `green`, `yellow`, `red`。状态：`open` 表示默认展开。支持嵌套。

```md
{% folding 查看内容 %}
被折叠的内容
{% endfolding %}

{% folding cyan open::默认打开 %}
打开状态的内容
{% endfolding %}
```

### 分栏标签tab

{% tabs tab-id %}
<!-- tab 标签一 -->
这是第一个标签页的内容
<!-- endtab -->
<!-- tab 标签二 -->
这是第二个标签页的内容
<!-- endtab -->
{% endtabs %}

```md
{% tabs tab-id %}
<!-- tab 标签一 -->
内容一
<!-- endtab -->
<!-- tab 标签二 -->
内容二
<!-- endtab -->
{% endtabs %}
```

### 诗文poetry

{% poetry 沙扬娜拉 author:徐志摩 date:1924年 footer:摘自《志摩的诗》 %}
最是那一低头的温柔，
像一朵水莲花不胜凉风的娇羞，
道一声珍重，道一声珍重，
那一声珍重里有蜜甜的忧愁——
沙扬娜拉！
{% endpoetry %}

```md
{% poetry 标题 author:作者 date:日期 footer:页脚 %}
诗文内容（支持 Markdown）
{% endpoetry %}
```

### 纸张paper

内部用 HTML 注释标记段落类型：

{% paper style:underline title:致橡树 author:舒婷 date:1977年3月27日 footer:摘自《双桅船》 %}

<!-- section 我如果爱你—— -->
绝不像攀援的凌霄花，借你的高枝炫耀自己；

<!-- section 我如果爱你—— -->
绝不学痴情的鸟儿，为绿荫重复单调的歌曲；

<!-- line right -->
也不止像泉源，常年送来清凉的慰藉。

{% endpaper %}

```md
{% paper style:underline title:标题 author:作者 date:日期 %}
<!-- section 章节标题 -->
章节内容
<!-- paragraph -->
段落内容
<!-- line right -->
右对齐行
{% endpaper %}
```

### 纵排诗歌reel

{% reel 赏花 author:李白 date:唐 footer:全唐诗 %}
花间一壶酒，独酌无相亲。
举杯邀明月，对影成三人。
{% endreel %}

```md
{% reel 赏花 author:李白 date:唐 footer:全唐诗 %}
花间一壶酒，独酌无相亲。
举杯邀明月，对影成三人。
{% endreel %}
```

---

### 目标管理

目标管理OKR（Objectives and Key Results）示例
可在OKR中嵌套其他组件

{% okr o1 %}

2088年的小目标：完成 Volantis 42.0 并发布上线
来自2088年末的复盘：已《基本》实现目标 {% emoji tieba huaji %}

<!-- okr kr1 percent:100 -->
重构 tag-plugins 和 wiki 系统
- 当 {% mark KR %} 进度为 100% 时，标签默认显示为 {% mark color:green 已完成 %}
- 当 {% mark KR %} 未设置进度时，默认为 {% mark 0% %}
- 当 {% mark O %} 未设置进度时，则显示所有 {% mark KR %} 进度平均值

<!-- okr kr2 percent:90 status:off_track -->
完成主要页面设计稿
{% Tabs align:left %}
<!-- tab 小提示1 -->
您可以在 _config.yml 文件中修改标签的颜色和文案
<!-- tab 小提示2 -->
您可以在 _config.yml 文件中增加任意的标签配置
{% endTabs %}

<!-- okr kr3 percent:-12 status:unfinished -->
完成前置准备工作（如果你知道答案，请在留言区帮帮我！🥹）
{% Checkbox 在咸水和海滩之间找一亩地 %}
{% Checkbox 求出圆周率后15位 %}
{% Checkbox 找出宇宙的终极逻辑 %}
{% Checkbox 去地狱里走两步 %}

<!-- okr kr-4 status:at_risk -->
开发、测试和发布
{% Image https://unpkg.com/volantis-static@0.0.1761982841160/media/org.volantis/blog/Logo-NavBar@3x.png height:64px 支持嵌套插入图片等其它简单组件 ratio:512/512 %}

{% endokr %}

```md
{% okr o1 %}

2088年的小目标：完成 Volantis 42.0 并发布上线
来自2088年末的复盘：已《基本》实现目标 {% emoji tieba huaji %}

<!-- okr kr1 percent:100 -->
重构 tag-plugins 和 wiki 系统
- 当 {% mark KR %} 进度为 100% 时，标签默认显示为 {% mark color:green 已完成 %}
- 当 {% mark KR %} 未设置进度时，默认为 {% mark 0% %}
- 当 {% mark O %} 未设置进度时，则显示所有 {% mark KR %} 进度平均值

<!-- okr kr2 percent:90 status:off_track -->
完成主要页面设计稿
{% Tabs align:left %}
<!-- tab 小提示1 -->
您可以在 _config.yml 文件中修改标签的颜色和文案
<!-- tab 小提示2 -->
您可以在 _config.yml 文件中增加任意的标签配置
{% endTabs %}

<!-- okr kr3 percent:-12 status:unfinished -->
完成前置准备工作（如果你知道答案，请在留言区帮帮我！🥹）
{% Checkbox 在咸水和海滩之间找一亩地 %}
{% Checkbox 求出圆周率后15位 %}
{% Checkbox 找出宇宙的终极逻辑 %}
{% Checkbox 去地狱里走两步 %}

<!-- okr kr-4 status:at_risk -->
开发、测试和发布
{% Image https://unpkg.com/volantis-static@0.0.1761982841160/media/org.volantis/blog/Logo-NavBar@3x.png height:64px 支持嵌套插入图片等其它简单组件 ratio:512/512 %}

{% endokr %}
```
---

## 多媒体

### inlineimage

这是 {% inlineimage https://gcore.jsdelivr.net/gh/volantis-x/cdn-emoji/aru-l/0000.gif %} 一段话。

```md
这是 {% inlineimage https://gcore.jsdelivr.net/gh/volantis-x/cdn-emoji/aru-l/0000.gif %} 一段话。
{% inlineimage https://gcore.jsdelivr.net/gh/volantis-x/cdn-emoji/aru-l/0000.gif height=40px %}
```

### image

参数：`width=300px`, `height=32px`, `alt=描述`, `bg=#f2f2f2`

```md
{% image 链接 width=300px alt=描述 bg=#f2f2f2 %}
```

### gallery

参数：`stretch`（拉伸填充）、方向 `left/center/right`、列数 `2~8`、`分组名`

```md
{% gallery %}
![描述](图片链接)
{% endgallery %}

{% gallery stretch::3::分组名 %}
![](图片1)
![](图片2)
{% endgallery %}
```

### swiper

参数：`width:min/max`（宽度）、`effect:cards/coverflow`（切换效果）

```md
{% swiper effect:cards %}
![](图片1)
![](图片2)
{% endswiper %}
```

### audio

```md
{% audio https://音频链接.mp3 %}
```

### video

`videos::列数` 支持 1~4 列网格布局

```md
{% video https://视频链接.mp4 %}

{% videos::2 %}
{% video 视频1 %}
{% video 视频2 %}
{% endvideos %}
```

### frame

设备外框的图片/视频，目前仅支持 `iphone11` 设备边框。`focus:top/bottom` 控制截取上半或下半。
{% Frame iphone11 img:https://res.xaox.cc/gh/cdn-x/wiki@main/prohud/toast/demo-loading.png video:https://res.xaox.cc/gh/cdn-x/wiki@main/prohud/toast/demo-loading.mp4 focus:top %}

```md
{% Frame iphone11 img:图片链接 video:视频链接 focus:top %}
```
---

## 交互类

### copy

对于单行内容，可以使用 copy 标签来实现复制功能：
{% copy curl -s https://sh.xaox.cc/install | sh %}
{% copy curl -s https://sh.xaox.cc/install | sh prefix:$ %}

可以设置 git:https 或者 git:ssh 或者 git:gh 来快速放置一个 git 仓库链接：
{% copy git:https volantis-x/hexo-theme-volantis %}
{% copy git:ssh volantis-x/hexo-theme-volantis %}
{% copy git:gh volantis-x/hexo-theme-volantis %}

```md
{% copy curl -s https://sh.xaox.cc/install | sh %}
{% copy curl -s https://sh.xaox.cc/install | sh prefix:$ %}
{% copy git:https volantis-x/hexo-theme-volantis %}
{% copy git:ssh volantis-x/hexo-theme-volantis %}
{% copy git:gh volantis-x/hexo-theme-volantis %}
```


### banner

见关于页面的示例
```md
{% banner 标题 副标题 bg:背景图 avatar:头像 link:跳转链接 %}
{% navbar 导航菜单 %}
{% endbanner %}
```

---

## 表情 emoji


在[emoji](https://volantis.js.org/v6/tag-plugins/emoji)中搜索想要的表情图标。
{% emoji blobcat attention %} {% emoji tieba huaji %} {% emoji aru-l 0190 %}

```md
{% emoji blobcat attention %} {% emoji tieba huaji %} {% emoji aru-l 0190 %}
```
如果对高度有特别要求，可以指定高度，例如：
<center>{% emoji tieba huaji height:1em %}{% emoji tieba huaji height:2em %}{% emoji tieba huaji height:3em %}{% emoji huaji party height:2em %}{% emoji tieba huaji height:1em %}</center>

---

## 盒子box

### 彩色代码块codeblock

设置 child:codeblock 并设置 color:颜色枚举 可以实现 10 种不同颜色的代码块，彩色代码块一般可以用在代码正确与错误的示范对比场景。

{% box child:codeblock color:green %}
  ```python
  import pandas as pd
  import numpy as np
  from scipy import stats, interpolate

  anomaly_elements = ['Ag', 'As', 'Au', 'Bi', 'Cu', 'Hg', 'Mo', 'Pb', 'Sb', 'Sn', 'W', 'Zn']
  zscores = {}
  ```
{% endbox %}

> 语法：`{% box child:codeblock color:颜色 %}` ... `{% endbox %}`，颜色可选 green/red/yellow/blue/cyan/purple 等。

### 嵌套多段代码块
将多个脚本嵌套在 box 标签内，每个脚本用不同的代码块表示。

{% box child:codeblock color:red %}
  ```python 脚本1
  import pandas as pd
  import numpy as np
  from scipy import stats, interpolate

  print("hello world")
  ```
  ```python 脚本2
  def kmo_test(data):
    """KMO检验"""
    corr = np.corrcoef(data.T)
    inv_corr = np.linalg.inv(corr)
    partial_corr = -inv_corr / np.sqrt(np.outer(np.diag(inv_corr), np.diag(inv_corr)))
    np.fill_diagonal(partial_corr, 1)
    
    sum_corr_sq = np.sum(np.square(corr)) - corr.shape[0]
    sum_partial_corr_sq = np.sum(np.square(partial_corr)) - partial_corr.shape[0]
    
    kmo = sum_corr_sq / (sum_corr_sq + sum_partial_corr_sq)
    
    kmo_i = np.zeros(corr.shape[0])
    for i in range(corr.shape[0]):
        sum_corr_i = np.sum(np.square(corr[i])) - 1
        sum_partial_corr_i = np.sum(np.square(partial_corr[i])) - 1
        kmo_i[i] = sum_corr_i / (sum_corr_i + sum_partial_corr_i)
    
    return kmo, kmo_i
  ```
{% endbox %}

