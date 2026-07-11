---
title: 特殊的阿拉伯文Unicode符号一览（上）
published: 2026-06-07
tags: 
- 语言
slug: arabic-special-symbols-1
---


:::note
截止目前（2026年2月24日），很多阿拉伯文字体对于阿拉伯文区块的覆盖率不高，因此文中会出现字符无法显示的情况。
为防止某些字符无法正常显示，这些字符会加上ا字符。
:::

文章内容以Unicode 17.0为准，阿拉伯字母包含7个区块。斜体的区块包含在下篇：

* 基本阿拉伯文
* 阿拉伯文补充
* 阿拉伯文拓展A、
* *阿拉伯文拓展B和C*
* *阿拉伯文表现形式A、B*

۞۩

## ؋
名称：`AFGHANI SIGN`

阿富汗货币阿富汗尼的符号。

## ؀
名称：`ARABIC NUMBER SIGN`

控制字符，在阿拉伯文早期编码中作为数字起始标记使用。现已弃用。当字符书写方向为右至左时就会以特殊方式渲染。如：ا ؀۱۲۳۴

## ؁
名称：`ARABIC SIGN SAHAH`

控制字符，标记年份开始。与前面的字符同样有特殊渲染方式：ا ؁۱۲۳۴

## 

ا ؂۱۲۳۴

ا ؀۱۲۳۴

## ٭
名称：`ARABIC FIVE POINTED STAR`

## ک
名称：`ARABIC LETTER KEHEH`

了解波斯语的人会对这个字符比较熟悉。

## ٵ ٶ ٷ ٸ
这些字符都是阿拉伯文版的哈萨克语中的字符，属于子区快*Digraphic letters for Kazakh*，目前仅中国的哈萨克族还在使用阿拉伯文书写的哈萨克语。

对照表：

| 阿拉伯文 | 西里尔文 | 拉丁文（2021） |
|-|-|-|
| ٴا | Әә | Ää |
|  ٴو | Өө | Öö |
| ٴۇ | Үү | Üü |
|  ٴى | Іі | Iı |


另外，这些字符的兼容分解形式的字符顺序是相反的，如ٵ的兼容分解形式为اٴ（ا排在前面），在这个子区块提到：

> These characters were encoded for Kazakh digraphs, but their compatibility decompsitions do not reflect the preferred order of representation.

字符的介绍中也有“preferred spelling is...”的说明，因此这些字符的兼容分解形式是错的，Unicode官方因此推荐使用两字符的形式（也就是   ٴ（`ARABIC LETTER HIGH HAMZA`）加上元音字母的形式）。

## ی
名称：`ARABIC LETTER FARSI YEH`

这个字符的独立式看上去和ى（`ARABIC LETTER ALEF MAKSURA`）没区别，但其后连式与前后连式多了两点。

| 名称 | 独立式 | 后连式 | 前后连式 | 前连式 |
|-|-|-|-|-|
| ALEF MAKSURA | ى | ىـ | ـىـ | ـى |
| FARSI YEH | ی | یـ | ـیـ | ـی |

实际上这个字符是波斯语中的ي，其独立式和前连式中的两点会消失。

## ـ
名称：`ARABIC TATWEEL`

阿拉伯延长符，Unicode名称得名于阿拉伯语تَطْوِيل。主要用于文本对齐排版和承载变音符号。[^1]

本文也使用此符号呈现字符的各种书写形式。

## ه ھ ہ ە
名称：
* `ARABIC LETTER HEH`
* `ARABIC LETTER HEH DOACHASHMEE`
* `ARABIC LETTER HEH GOAL`
* `ARABIC LETTER AE`

| 名称 | 独立式 | 后连式 | 前后连式 | 前连式 |
|-|-|-|-|-|
| HEH | ه | هـ | ـهـ | ـه |
| HEH DOACHASHMEE | ھ | ھـ | ـھـ | ـھ |
| HEH GOAL | ہ | ہـ | ـہـ | ـہ |
| AE | ە | 无 | 无 | ـە |

ھ ە则是突厥语族中

## ۝
古兰经中的章节结束符号，通常以里面加数字的形式使用，如ا ۝١

目前似乎大多数字体无法正确渲染中间带数字的形式，Segoe UI是为数不多能正确渲染的字体之一。

## ࢻ、ࢼ、ࢽ和ࣄ
名称：
* `ARABIC LETTER AFRICAN FEH`
* `ARABIC LETTER AFRICAN QAF`
* `ARABIC LETTER AFRICAN NOON`
* `ARABIC LETTER AFRICAN QAF WITH THREE
DOTS ABOVE`

| 名称 | 独立式 | 后连式 | 前后连式 | 前连式 |
|-|-|-|-|-|
| FEH | ࢻ | ࢻـ | ـࢻـ | ـࢻ |
| QAF | ࢼ | ࢼـ | ـࢼـ | ـࢼ |
| NOON | ࢽ | ࢽـ | ـࢽـ | ـࢽ |
| QAF WITH THREE DOTS ABOVE | ࣄ | ࣄـ | ـࣄـ | ـࣄ |


# 𐻑𐻒𐻓
名称：
* `ARABIC LIGATURE ALAYHAA AS-SALAATU
WAS-SALAAM`
* `ARABIC LIGATURE ALAYHIM AS-SALAATU
WAS-SALAAM`
* `ARABIC LIGATURE ALAYHIMAA AS-SALAATU
WAS-SALAAM`

TODO: 𐻔 𐻕𐻖𐻗 𐻘

## ﯃
名称：`ARABIC LIGATURE JALLA WA-ALAA`

TODO: ﯅﯆﯇

## ﵀
名称：`ARABIC LIGATURE RAHIMAHU ALLAAH`

TODO: ﵁﵂﵃﵄﵅

## ﶐﶑
TODO: 名称

[^1]: <https://en.wikipedia.org/wiki/Kashida>