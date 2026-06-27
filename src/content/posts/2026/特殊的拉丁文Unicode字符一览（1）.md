---
title: 特殊的拉丁文Unicode字符一览（1）
published: 2026-06-23
tags: 
- Unicode
slug: special-latin-letters-1
---

:::note
本文不包含同区块的控制字符、空格字符和标点符号信息。
:::

拉丁文包含13个区块：
* 基本拉丁文（ASCII）
* Latin-1补充
* 拓展A、B、C、D、E、F、G
* 附加拓展
* IPA拓展
* 音标拓展
* 音标拓展补充

本文讲的是基本拉丁文、Latin-1补充和拓展A、B区块的内容，其他区块中的字符也有可能因关联提到。

## ªº
名称：
* `FEMININE ORDINAL INDICATOR`
* `MASCULINE ORDINAL INDICATOR`

罗曼语族语言的序数指示符。如

这两个字母与a和o分别为兼容等价关系。

## Þþ
名称：`LATIN * LETTER THORN`

这是一个曾用于古诺斯克语、古英语，现用于冰岛语和语言转写的字符。这个字母源于卢恩字母ᚦ，之后被连字th替代。在冰岛语中通常表示[θ̠]音。

## ĎďĽľŤť
名称：
* `LATIN CAPITAL LETTER D WITH CARON`
* `LATIN SMALL LETTER D WITH CARON`
* `LATIN CAPITAL LETTER L WITH CARON`
* `LATIN SMALL LETTER L WITH CARON`
* `LATIN CAPITAL LETTER T WITH CARON`
* `LATIN SMALL LETTER T WITH CARON`

虽然这三个字母有的加的是ˇ（`CARON`），有的加的是单引号，但这些字符的名称后缀都是`WITH CARON`，兼容分解形式都是基础字母加上`COMBINING CARON`。

> the form using apostrophe is preferred in typesetting

## ÐĐƉ
名称：
* `LATIN CAPITAL LETTER ETH`
* `LATIN CAPITAL LETTER D WITH STROKE`
* `LATIN CAPITAL LETTER AFRICAN D`

虽然三者外观相同，但分别代表的是三个不同字母的大写：

* Ðð，字母ETH，是一个曾被古英语，现在被冰岛语、法罗语等语言使用的字符。小写形式也被用于国际音标表示同样的发音。
* Đđ则被用于萨米语、越南语和塞尔维亚（—克罗地亚）语的拉丁字母版本（同西里尔字母ђ）。
* Ɖɖ作用同名称，用于非洲的语言，小写形式也在国际音标中表示卷舌爆发音。

## ĢģŅņĶķĻļŖŗ
名称：
* `LATIN CAPITAL LETTER G WITH CEDILLA`
* `LATIN SMALL LETTER G WITH CEDILLA`
* `LATIN CAPITAL LETTER N WITH CEDILLA`
* `LATIN SMALL LETTER N WITH CEDILLA`
* `LATIN CAPITAL LETTER K WITH CEDILLA`
* `LATIN SMALL LETTER K WITH CEDILLA`
* `LATIN CAPITAL LETTER L WITH CEDILLA`
* `LATIN SMALL LETTER L WITH CEDILLA`
* `LATIN CAPITAL LETTER R WITH CEDILLA`
* `LATIN SMALL LETTER R WITH CEDILLA`

这些字母虽然外观都是基础字母加上逗号，但名称结尾都是`WITH CEDILLA`，并且兼容分解形式也是相应字母加上`COMBINING CEDILLA`（¸的结合版本）。

之所以这样，是因为这些字母用于拉脱维亚语中，这些字母加上逗号表示对于辅音的软腭化，因此被早期编码标准规为了与ç一类的字符,在官方文档中提到：

> despite their names, this pair of characters should normally be displayed with a comma below

也就是说这些字符应该是下面加上逗号的形式。其中的一个例外是ģ，因为在底部加上逗号会造成排版问题，所以这个逗号以翻转的形式加在了上面。

另外，罗马尼亚语的字符也类似，但由于其他语言有类似ş的字符，因此罗马尼亚语使用的ș的名称与兼容分解形式是符合外形的。

## İı
名称：
* `LATIN CAPITAL LETTER I WITH DOT ABOVE`
* `LATIN SMALL LETTER DOTLESS I`

这些字母用于土耳其语等一些突厥语言的正字法中，用于İi，Iı两个字母。

顺带一提，由于这与主要语言以Ii为一对字母是冲突的，这成为了一个麻烦的本地化问题。现有解决以Javascript为例有：

* [.toLocaleUpperCase](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/toLocaleLowerCase)
* [Intl.Collator](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Intl/Collator)

## Ĳĳ
名称：
* `LATIN CAPITAL LIGATURE IJ`
* `LATIN SMALL LIGATURE IJ`

荷兰语ij连字。在荷兰语中，ij为一个字母，表示元音[ɛi]。

## ĸ
名称：`LATIN SMALL LETTER KRA`

这是一个用于格陵兰语和拉布拉多因纽特语方言的字母，在格陵兰语中其大写为*K'*。在1973年格陵兰语拼写改革后便被q代替。

此字符也在国际音标中表示清小舌塞音。[^1]

## ſ
名称：`LATIN SMALL LETTER LONG S`

这个字符是s在历史上的变体，是s在单词开头和中间的写法。由于易与字母f混淆，逐渐变得不常用。

顺带一提，德语中使用的ß字母本来就是ſs的连字。[^2]

## ƂƃƄƅƋƌƧƨƼƽƜɯ
LATIN CAPITAL LETTER B WITH TOPBAR
LATIN SMALL LETTER B WITH TOPBAR
LATIN CAPITAL LETTER TONE SIX
LATIN SMALL LETTER TONE SIX
LATIN CAPITAL LETTER D WITH TOPBAR
LATIN SMALL LETTER D WITH TOPBAR
LATIN CAPITAL LETTER TONE TWO
LATIN SMALL LETTER TONE TWO
LATIN CAPITAL LETTER TONE FIVE
LATIN SMALL LETTER TONE FIVE
LATIN CAPITAL LETTER TURNED M
LATIN SMALL LETTER TURNED M

## ƏəƎǝ

## Ƒƒ

## Ɩɩ

## Ƕƕ

用于转写哥特字母𐍈，表示[hʷ]或[ʍ]发音。

## Ɣɣ

## Ƞƞ

## Ƣƣ

这个字母曾用于一些突厥语系语言的拉丁文正字法中，如阿塞拜疆语，在我之前写的[从旧字典发现的旧拉丁维文](../old-latin-uyghur/)中提到的“新维文”也使用了这些字符。现在已被Ğğ等字符代替。

## Ʀʀ

曾被古诺斯克语使用的字符，也是卢恩字母ᛦ的转写。小写形式也在国际音标中表示小舌颤音。

## Ʃʃ



## Ʊʊ

## Ƿƿ
ᚹ

## ǀǁǃ

**这个字符不是竖线、感叹号。**

## ǄǅǆǇǈǉǊǋǌ

## ȷ

## Ȣȣ

## ȸȹ

[^1]: <https://en.wikipedia.org/wiki/%C4%B8>

[^2]: <https://www.qiuwenbaike.cn/wiki/长s>

[^3]: <https://www.qiuwenbaike.cn/wiki/Ʀ>