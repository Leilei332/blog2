---
title: 特殊的阿拉伯文Unicode符号一览
published: 2025-12-23
updated: 2026-03-20
tags: 
- 语言
slug: arabic-special-symbols
---


:::note
截止目前（2026年2月24日），很多阿拉伯文字体对于阿拉伯文区块的覆盖率不高，因此文中会出现字符无法显示的情况。
为防止某些字符无法正常显示，这些字符会加上ا字符。
:::

文章内容以Unicode 17.0为准，阿拉伯字母包含7个区块：

* 基本阿拉伯文
* 阿拉伯文补充
* 阿拉伯文拓展A、B和C
* 阿拉伯文表现形式A、B

fa:﴾﴿

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

ا ؂۱۲۳۴

ا ؀۱۲۳۴

## ٭
名称：`ARABIC FIVE POINTED STAR`

## ک
名称：`ARABIC LETTER KEHEH`

了解波斯语的人会对这个字符比较熟悉。

## ی
名称：`ARABIC LETTER FARSI YEH`

这个字符的独立式看上去和ى（`ARABIC LETTER ALEF MAKSURA`）没区别，但其后连式与前后连式多了两点。

| 名称 | 独立式 | 后连式 | 前后连式 | 前连式 |
|-|-|-|-|-|
| ALEF MAKSURA | ى | ىـ | ـىـ | ـى |
| FARSI YEH | ی | یـ | ـیـ | ـی |

## ـ
名称：`ARABIC TATWEEL`

阿拉伯延长符，Unicode名称得名于阿拉伯语تَطْوِيل。主要用于文本对齐排版和承载变音符号。[^2]

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

以下均为《古兰经》中所使用的符号

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

## ﷼
* 位置：`U+FDFC`
* 名称：`RIAL SIGN`

将其拆开得到ریال。里亚尔，沙特阿拉伯等国所使用的货币符号。

## ﷺ
* 位置：`U+FDFA`
* 名称：`ARABIC LIGATURE SALLALLAHOU ALAYHE WASALLAM`

阿拉伯语合字，将其拆开得到：

> صلى الله عليه وسلم

意思为“愿真主赐福他并使他平安”。

## ﷻ

* 位置：`U+FDFB`
* 名称：`ARABIC LIGATURE JALLAJALALOUHOU`

阿拉伯语合字，拆开后得到：

> جل جلاله

意思为“愿祂的尊荣崇高”。

## ﷲ
* 位置：`U+FDF2`
* 名称：`ARABIC LIGATURE ALLAH ISOLATED FORM`

阿拉伯文الله的合字，指真主安拉。

## ﷴ
* 位置：`U+FDF4`
* 名称：`ARABIC LIGATURE MOHAMMAD ISOLATED FORM`

阿拉伯文محمد的合字，也就是穆罕默德。

## ﷽

信息
: 名称：`ARABIC LIGATURE BISMILLAH AR-RAHMAN AR-RAHEEM`
: 位置：`U+FDFD`

~~这个字符是唯一无法用NFKC拆开的阿拉伯文合字~~，内容为：

> بِسْمِ ٱللَّهِ ٱلرَّحْمَـٰنِ ٱلرَّحِيمِ

意思为“奉至仁至慈的真主之名”。这个宗教短语还有一个名称叫*太斯米*。[^1]

## ﷾
名称：`ARABIC LIGATURE SUBHAANAHU WATAAALAA`

[^1]: <https://www.qiuwenbaike.cn/wiki/%E5%A4%AA%E6%96%AF%E7%B1%B3>

[^2]: <https://en.wikipedia.org/wiki/Kashida>