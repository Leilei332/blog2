---
title: 特殊的拉丁文Unicode字符一览（1）
published: 2026-06-28
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

顺带一提，德语中使用的ß字母本来是ſs的连字。[^2]

## ƂƃƄƅƋƌƧƨƼƽƜɯ
名称：

* `LATIN CAPITAL LETTER B WITH TOPBAR`
* `LATIN SMALL LETTER B WITH TOPBAR`
* `LATIN CAPITAL LETTER TONE SIX`
* `LATIN SMALL LETTER TONE SIX`
* `LATIN CAPITAL LETTER D WITH TOPBAR`
* `LATIN SMALL LETTER D WITH TOPBAR`
* `LATIN CAPITAL LETTER TONE TWO`
* `LATIN SMALL LETTER TONE TWO`
* `LATIN CAPITAL LETTER TONE FIVE`
* `LATIN SMALL LETTER TONE FIVE`
* `LATIN CAPITAL LETTER TURNED M`
* `LATIN SMALL LETTER TURNED M`

都是壮语曾使用的字符，在1982年被ASCII拉丁字符代替：

| 旧版 | 新版 |
|-|-|
| Ƃ ƃ | Mb mb |
| Ƅ ƅ | H h |
| Ƌ ƌ | Nd nd |
| Ƨ ƨ | Z z |
| Ƽ ƽ | Q q |
| Ɯ ɯ | W w |

## ƍ

曾用于表示唇化齿龈擦音，现已被/zʷ/和/z̫/代替。

## ƏəƎǝ
名称：

* `LATIN CAPITAL LETTER SCHWA`
* `LATIN SMALL LETTER SCHWA`
* `LATIN CAPITAL LETTER REVERSED E`
* `LATIN SMALL LETTER TURNED E`
 
虽然两者的小写形式的外观相似，但表示的是不同字母：

* Əə用于许多突厥语系语言的正字法中，如阿塞拜疆语，“新维文”等。
* Ǝǝ则用于[泛尼日利亚字母](https://www.qiuwenbaike.cn/wiki/泛尼日利亚字母)

## Ƒƒ
名称：

* `LATIN CAPITAL LETTER F WITH HOOK`
* `LATIN SMALL LETTER F WITH HOOK`

## Ɩɩ
名称：

* `LATIN CAPITAL LETTER IOTA`
* `LATIN SMALL LETTER IOTA`

注意：这个字符源于希腊字母Iota（ι），但不是希腊字母。

用于非洲语言的字符，如Gurunɛ，Kabiyé和Mossi。同时小写形式曾在国际音标中表示元音，之后被ɪ代替。

## Ƕƕ
名称：

* `LATIN CAPITAL LETTER HWAIR`
* `LATIN SMALL LETTER HV`

用于转写哥特字母𐍈，表示[hʷ]或[ʍ]发音。

## Ɣɣ
名称：

* `LATIN CAPITAL LETTER GAMMA`
* `LATIN SMALL LETTER GAMMA`

## Ƞƞ
名称：

* `LATIN CAPITAL LETTER N WITH LONG RIGHT LEG`
* `LATIN SMALL LETTER N WITH LONG RIGHT LEG`

## ƛ

## Ɵɵ

## Ƣƣ
名称：

* `LATIN CAPITAL LETTER OI`
* `LATIN SMALL LETTER OI`

这个字母曾用于一些突厥语系语言的拉丁文正字法中，如阿塞拜疆语，在我之前写的[从旧字典发现的旧拉丁维文](../old-latin-uyghur/)中提到的“新维文”也使用了这些字符。现在已被Ğğ等字符代替。

## Ʀʀ
名称：

* `LATIN LETTER YR`
* `LATIN LETTER SMALL CAPITAL R`

曾被古诺斯克语使用的字符，也是卢恩字母ᛦ的转写。小写形式也在国际音标中表示小舌颤音。

## Ʃʃ
名称：

* `LATIN CAPITAL LETTER ESH`
* `LATIN SMALL LETTER ESH`



## Ʊʊ
名称：

* `LATIN CAPITAL LETTER UPSILON`
* `LATIN SMALL LETTER UPSILON`

## Ƹƹ

## ƺ

## ƻ

虽然这个字符的外观是一个中间有线的2，但是这个字符实际上是一个音标，曾用于表示/dz/音，之后被/ʒ/和/dz/代替。

## Ƿƿ
名称：

* `LATIN CAPITAL LETTER WYNN`
* `LATIN LETTER WYNN`

ᚹ

## ǀǁǃ
名称：

* `LATIN LETTER DENTAL CLICK`
* `LATIN LETTER LATERAL CLICK`
* `LATIN LETTER RETROFLEX CLICK`

**这些字符不是|（`VERTICAL LINE`）、!（`EXCLAMATION MARK`）。**

## ǄǅǆǇǈǉǊǋǌ
名称：

* `LATIN CAPITAL LETTER DZ WITH CARON`
* `LATIN CAPITAL LETTER D WITH SMALL LETTER Z WITH CARON`
* `LATIN SMALL LETTER DZ WITH CARON`
* `LATIN CAPITAL LETTER LJ`
* `LATIN CAPITAL LETTER L WITH SMALL LETTER J`
* `LATIN SMALL LETTER LJ`
* `LATIN CAPITAL LETTER NJ`
* `LATIN CAPITAL LETTER N WITH SMALL LETTER J`
* `LATIN SMALL LETTER NJ`

均为南斯拉夫语族的语言使用的拉丁字母

## Ȝȝ


## Ȣȣ
名称：

* `LATIN CAPITAL LETTER OU`
* `LATIN SMALL LETTER OU`

## ȸȹ
名称：

* `LATIN SMALL LETTER DB DIGRAPH`
* `LATIN SMALL LETTER QP DIGRAPH`

[^1]: <https://en.wikipedia.org/wiki/%C4%B8>

[^2]: <https://www.qiuwenbaike.cn/wiki/长s>

[^3]: <https://www.qiuwenbaike.cn/wiki/Ʀ>
