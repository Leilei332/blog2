---
date: "\\<2022-12-02 Fri 20:40\\>"
description: 安卓上的Rime
title: Trime体验
---

```{=org}
#+filetags: @软件 @开源 Android
```
第一次体验Rime是在Linux里使用ibus-rime，不过由于体验时问题比较多所以没有继续使用。最近在Fdroid上看到了Rime的安卓版：Trime（又叫同文输入法），准备再次尝试一下这个开源的输入法。

这一整篇文章都是用Trime输入法打出来的。

# 配置

Rime只是一个输入法引擎，所以默认是不带输入法的，需要从Github上下载一个配置来用。我一开始用的是[rimerc](https://github.com/Bambooin/rimerc)，里面默认包含了"明月拼音输入法。

可惜的是这个输入法默认只支持繁体中文。为了解决这个问题，Rime的开发者又弄了一个 `opencc` 项目，这个开源工具支持转换文字和词语，目前Trime已经内置了这个工具。只需在配置文件中启用即可。

Rime的配置文件用的是yaml语法。rimerc的Trime版本的明月拼音有一个简繁开关，但没有用，解决的方法是在 `luna_pinyin.schema.yaml` 中加入以下内容：

``` yaml
simplifier:
    opencc_config: tw2sp.json
      option_name: simplification
```

不过这样还是不能启动时使用简体字，所以我换到了[四叶草简体拼音输入法](https://github.com/fkxxyz/rime-cloverpinyin)，默认支持简体。

注意这个输入法opencc里的文件不能复制进去，否则会导致部署时发生崩溃。

# 一些独特的功能

在用Trime之前我用的是谷歌拼音输入法。Trime相比于谷歌拼音在一些小地方做得不错。

## 快捷操作

Trime为剪切，复制，粘贴三个操作设置了快捷键。

- `x` ：剪切
- `c` ：复制
- `v` ：粘贴

之前我进行粘贴等操作都是长按屏幕再点击粘贴，而Trime让操作像Vim[^1]一样方便。

## 个性化

### 主题

Trime内置主题和配色功能，默认带了主题 `trime`
和 `tongwenfeng` 。

主题和大多数输入法的皮肤功能一样，将主题的yaml文件和资源文件拖进rime文件夹就可以用。Trime内置的主题也内置了很多配色方案，这里推荐的配色方案是 *暗堂 Dark Temple* 。

在GitHub上也有一些不错的主题，如[单静](https://github.com/cxcn/danjing)。

### 音效

Trime内置音效自定义，不过不常用。

## 草稿箱和剪贴板

这也是Trime中的一个很重要的功能。Trime会将一些输入历史自动记录到草稿箱，把剪贴的历史记录到剪贴版，可以在键盘中的 *更多* 里看到[^2]。

如果不想让所有记录都记录到草稿箱，可以设置通过应用包名或者正则表达式过滤。

在Trime的设置界面中可以管理草稿和剪贴板历史记录。

# 问题

由于Trime 3.2.9的问题比较大，所以这里推荐用3.2.8版本。

## ~~占用较大~~

Trime的性能相对于默认的华为输入法和谷歌拼音输入法比较一般，有时会出现手机开机启动后Trime还没有启动，导致调不出输入法。另外在v1.3.9版本崩溃的频率非常高，经常会出现无法启动的问题。

## 悬浮窗位置

在Android5上的拼音悬浮窗显示在左下角，而不是键盘上方。

目前唯一的解决方法是关闭悬浮窗， **嵌入式编辑模式** 选择编码。

## 一些字符不能显示

更换字体（比如Noto Sans CJK）。

在rime目录新建 `fonts` 目录，将字体文件放入（比如NotoSansCJKsc-Regular.ttf），然后找到要更改的主题，新建一个配置文件（比如 `tongwenfeng.trime.yaml` 的配置文件是 `tongwenfeng.trime.custom.yaml` ）在里面加入：

:::: captioned-content
::: caption
更换字体为Noto Sans CJK SC
:::

``` yaml
patch:
    "style/key_font": NotoSansCJKsc-Regular.ttf
```
::::

具体可以看[trime.yaml详解](https://github.com/osfans/trime/wiki/trime.yaml%25E8%25A9%25B3%25E8%25A7%25A3)

## 手写支持

由于Rime框架本身就是为键盘设计的，所以从根本上就不支持手写输入，目前能弄出来的手写输入法也只能和Rime独立，所以有手写需求就没必要用Trime了。

# 总结

目前Trime最大的问题就是性能问题。在较老的手机上的启动非常慢，有时甚至需要手动打开启动器的设置界面才能用，相比较而言谷歌拼音输入法是可以随便调用，非常流畅。

不过抛开这些，Trime作为一个开源输入法，能实现很多大厂输入法的功能，还是很不错的。

- [Rime输入法官网](https://rime.im)
- [Fdroid上的Trime](https://f-droid.org/zh_Hans/packages/com.osfans.trime/)

[^1]: Vim中是 `d` `y` `p`

[^2]: 这个页面的设计很奇怪，返回要在顶端才能看到。
