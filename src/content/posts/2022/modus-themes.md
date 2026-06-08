---
date: "\\<2022-12-23 周五 17:11\\>"
description: Modus Themes
title: 一个不错的Emacs主题
---

```{=org}
#+filetags: Emacs @编程
```
用过很多Emacs主题，做得不错的主题有 `doom-themes` ，[ef-themes](elpa:ef-themes)。其中 `doom-themes` 里面有很多不错的配色，比如Material，Gruvbox，Miramare。不过适配最广的还是[modus-themes](elpa:modus-themes)。

之前用的是 `doom-themes` 里面的Gruvbox，虽然配色很不错，但是对于一些类似 `fido-mode` 等类似工具的支持不是很好，里面对于输入的高亮匹配字符只显示为粗体，没有颜色。 `ef-themes` 和 `modus-themes` 的作者是同一个人，但是 `ef-themes` 对 `vc` 工具的颜色适配不行。

`modus-themes` 颜色配置用基于 *WCAG AAA* ，非常淳朴，虽然没上两个主题好看，但是提供了很多自定义选项，所以对于系统的组件的主题支持很广泛。

# 安装

`modus-themes` 需要Emacs版本最低为27.1。在Emacs 28.1的版本已经自带了 `modus-themes` 主题，而27.1版本可以通过package.el的elpa安装[^1]，在Debian里面也有一个[elpa-modus-themes](deb:elpa-modus-themes)包，可以用自带的包管理器安装。

加载主题需要以下代码，以里面自带的暗黑主题 `modus-vivendi` 为例：

``` commonlisp
(load-theme 'modus-vivendi t)
(modus-themes-load-vivendi)
```

# 设置

`modus-themes` 的默认主题不是很好看，不过可以通过设置主题提供的选项来达到满意的效果，这些选项需要在加载主题前设置好。

![modus-vivendi主题，左侧为原版，右侧为调整后](images/modus_preview.png)

首先根据[官网](https://protesilaos.com/emacs/modus-themes)的推荐设置，将F5绑定为切换亮色和暗色主题的按键。

``` commonlisp
(define-key global-map (kbd "<f5>") #'modus-themes-toggle)
```

## `Mode-line` 设置

`modus-themes` 默认会给mode-line加上一个白色的细线边框，不是很好看，通过自定义变量 `modus-themes-mode-line` 可以更改。

``` commonlisp
(setq modus-themes-mode-line '(borderless))
```

另外给列表加上 `accented` 可以让mode-line变为蓝色。

## 标签栏设置

目前用下来几乎所有的主题对Emacs的标签页支持（ `tab-bar-mode` ）的支持都一般。 `modus-theme` 默认设置标签栏是黑色，不过把选项 `modus-themes-tab-bar-accend` 设置为t可以让标签栏变为蓝色。

## 链接

`modus-themes` 默认的链接样式还行，像其他主题一样。不过我用了 `ef-themes` 之后感觉将链接的下划线设置为灰色比较美观一些，设置 `modus-themes-links` 为 `neutral-underline` 就行了

## 标题样式

`modus-themes` 标题的样式默认非常丑，不过也很好解决。 `modus-themes-headings` 的 `rainbow` 选项可以将所有标题变成彩虹色，给所有标题加上 `rainbow` 属性就行了。

``` commonlisp
(setq modus-themes-headings '((t . (rainbow))))
```

还有一个实用的选项 `modus-themes-scale-headings` ，可以让各级标题的文字大小不同。

## `fido-mode` 等组件

`modus-themes` 默认对补全组件的匹配高亮显示支持不错，但是只将文字变为蓝色和粉色这两种颜色，不是很美观。将 `modus-themes-completions` 设置为 `opinionated` 可以换成一个更好看的蓝色和紫色的背景。

## 其他

在很多主题中都会出现有的地方字体不正常的问题，这是因为有的地方用的Face[^2]用的是 `fixed-pitch` 和 `variable-pitch` ，而不是 `default` 。所以要给这些单独设置字体。

:::: captioned-content
::: caption
以"等距更纱黑体"为例
:::

``` commonlisp
(custom-set-faces
 ;; custom-set-faces was added by Custom.
 ;; If you edit it by hand, you could mess it up, so be careful.
 ;; Your init file should contain only one such instance.
 ;; If there is more than one, they won't work right.
 '(default ((t (:family "等距更纱黑体 SC" :foundry "outline" :slant normal :weight normal :height 110 :width normal))))
 '(fixed-pitch ((t (:family "等距更纱黑体 SC"))))
 '(variable-pitch ((t (:family "等距更纱黑体 SC")))))
```
::::

`doom-themes` 没有这个问题。 `modus-themes` 对于这个问题也提供了一个选项。将 `modus-themes-no-mixed-fonts` 设置为t，就不会出现这个问题。

:::: captioned-content
::: caption
其他配置
:::

``` commonlisp
(setq modus-themes-org-blocks 'gray-background)
(setq modus-themes-no-mixed-fonts t)
(setq modus-themes-intense-hl-line t)
```
::::

# Footnotes

[^1]: `M-x package-install RET modus-themes RET`

[^2]: 见[Faces](info:emacs#Faces)
