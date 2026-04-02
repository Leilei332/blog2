---
title: 特殊的希腊Unicode符号一览
published: 2026-02-04
updated: 2026-04-01
tags: 
- Unicode
slug: special-greek-symbols
---

:::note
此文不包含关于科普特文的信息。
:::

希腊文字母包含两个区块：

* 希腊文
* 希腊文拓展
* 古希腊数字

另外，某些不被Unicode算作希腊文但与其有关的符号也会在本文提到。

## Ͱͱ
名称：`GREEK * LETTER HETA`

## Ͳͳ
名称：`GREEK * LETTER ARCHAIC SAMPI`

## ʹ͵
名称：`GREEK NUMERAL SIGN`和`GREEK LOWER NUMERAL SIGN`

希腊语中标记数字的符号，如**Αʹ**表示1，**͵Α**表示1000[^1]。对ʹ进行四种归一化后得到ʹ（`MODIFIER LETTER PRIME`），字体也通常将两者渲染为相同的外观。

## ϜϝͶͷ

## Ϳϳ
名称：`GREEK * LETTER YOT`

曾在希腊语中表示/j/音，也就是德语中J的发音。外观通常与拉丁字母Jj相同。[^4]

## ϲͻͼͽϹϽϾϿ
均为希腊字母Σσς的变体，被成为“弯月形Sigma”。Ϲϲ在古代使用，现代也作为装饰使用。

剩下的字符都曾被用于修订。Ͼͼ曾被用于表示标记行位置有误，Ͻͻ用于标记错位的文本行，Ͽͽ用于表示该行后的内容要重新排序。Ͻͻ在公元前1世纪末期也用作缩写，表示自身名字与父名相同。[^2]

字母Ϲ和ϲ进行NFKC或NFKD归一化后会得到Σ和σ。

## ΄
名称：`GREEK TONOS`

希腊语变音符号，表示重读。对其进行NFKC或NFKD归一化后会得到 ́（`COMBINING ACUTE ACCENT`）。

## ;
名称：`GREEK QUESTION MARK`

希腊语中的问号。虽然与;（`SEMICOLON`）外观相同，两者严格说算与亚美尼亚语句号类似的同姓异义字符，~~但奇怪的是对其进行四种归一化后会得到;~~。官方文档推荐使用;（`SEMICOLON`）字符。

与µ不同，浏览器将两者视为不同字符。

## ·
名称：`GREEK ANO TELEIA`

希腊文中的中点符号，曾被用于表示分号，现在用法与普通中点相同。对其进行四种正常化会得到·（`MIDDLE DOT`）。[^3]

官方文档中推荐使用·（`MIDDLE DOT`）字符。

## Ϗϗ
希腊语连字，相当于και，表示“和”。[^5]

## ϐϑϰϖ

## Ϙϙ
名称：`GREEK * LETTER ARCHAIC KOPPA`

## Ϛϛ

## Ϟϟ

## Ϡϡ

## ϰ

## 古希腊数字区块

𐅄𐅦𐅨𐅩

## 其他

### µ
名称：`MICRO SIGN`

虽然外观与μ（`GREEK SMALL LETTER MU`）一致，但编码不同。有趣的是，µ的编码的位置位于Latin-1 Supplement这个区块，非常靠前。将其进行NFKC或NFKD归一化之后就会得到μ，浏览器的搜索功能也将两者视为相同字符。

### Ω
名称：`OHM SIGN`

### ∆
名称：`INCREMENT`

### ∏
名称：`N-ARY PRODUCT`

### ∑
名称：`N-ARY SUMMATION`


[^1]: <https://en.wikipedia.org/wiki/Greek_numerals#Isopsephy>

[^2]: <https://en.wikipedia.org/wiki/Sigma#Lunate_sigma>

[^3]: <https://leonidas.net/greek-type-design/examples-of-ano-teleia-use/>

[^4]: <https://en.wikipedia.org/wiki/J#Greek_letter_Yot>

[^5]: <https://en.wikipedia.org/wiki/Kai_(conjunction)#Ligature>