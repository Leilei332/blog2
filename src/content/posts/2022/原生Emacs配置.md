---
title: 原生Emacs配置
published: 2022-07-03
updated: 2022-07-17
slug: tw2022-vanilla-emacs-config
tags: 
- Tiddlywiki 2022归档
- Emacs
---


换到原生Emacs后，为了给org-mode配置一个比较好的环境，对Emacs进行了一番配置。

## 配置包管理器
Emacs默认支持用外部源装插件，用下面代码就可以激活：

```lisp
(require 'package) ;; 这一行似乎不用加
(setq package-archives '(("gnu"   . "http://mirrors.tuna.tsinghua.edu.cn/elpa/gnu/")
                         ("melpa" . "http://mirrors.tuna.tsinghua.edu.cn/elpa/stable-melpa/")))
(package-initialize)
```
目前对于外部插件的需求不是很大，只要三个包：

* ~~[gotham-theme](https://depp.brause.cc/gotham-theme) Gotham主题~~
* [doom-themes](https://github.com/doomemacs/themes) Doom Emacs自带主题（推荐）
* [org-superstar](https://github.com/integral-dw/org-superstar-mode) 美化org文件的标题（不推荐用[org-bullets](https://github.com/sabof/org-bullets)，因为这个插件很久没更新而且观感没org-superstar好）
* [htmlize](https://github.com/hniksic/emacs-htmlize) 将buffer转换为HTML（Debian上可以用`sudo apt install elpa-htmlize`安装）

这些插件都可以在[Stable Melpa](https://stable.melpa.org)，所以个人推荐用更稳定的Stable Melpa代替[Melpa](https://melpa.org)

## 功能配置
Emacs默认开启菜单栏，工具栏，不简洁，所以禁用菜单栏和工具栏。

```lisp
(tool-bar-mode 0)
(menu-bar-mode 0)
```

另外，在Buffer内还会显示滚动条，所以也要禁用。

```lisp
(scroll-bar-mode 0)
```

`menu-bar-mode`对初次上手Emacs非常有帮助，推荐手动<kbd>M-x</kbd>开启

---

鼠标悬停在某些地方会显示Tooltip，显示效果不好，所以禁用Tooltip：

```lisp
(tooltip-mode 0)
```

---

在每个buffer底部会有一个mode-line，里面可以显示org-clock，org-timer等信息。Emacs默认有一些对mode-line的特殊显示模式。

mode-line默认会显示行数，要默认显示列数在初始化文件加入：

```lisp
(column-number-mode 1)
```

开启`winner-mode`，支持把窗口改动撤销：

```lisp
(winner-mode 1)
```

按<kbd>C-c LEFT</kbd>就可以撤销窗口改动。

### 显示电池
```lisp
(display-battery-mode 1)
```
Emacs默认支持显示电池，可以在mode-line里看到百分比以及充电情况，比较有用。

下面这个代码可以在mode-line显示时间，不过由于大多数系统都在任务栏显示时间，所以没什么用，还会占用mode-line空间

```lisp
(display-time-mode 1)
```

---

TODO: 本人默认喜欢把Emacs最大化，在[[org-mode一些配置]]中可以更改`dotspacemacs-maximized-at-startup`来自动最大化。原生Emacs可以用一个内置函数来最大化：

```lisp
(toggle-frame-maximized)
```
---
开启Emacs自动补全括号：

```lisp
(electric-pair-mode 1)
```

## 其他
Emacs可以保存当前的窗口列表，开启`desktop-save-mode`即可，在org-mode里非常有用。

```lisp
(desktop-save-mode 1)
```
编辑文件时Emacs会产生**文件名~**这种备份文件，设置为不产生备份文件：

```lisp
(setq make-backup-files nil)
```
如果光标到了尽头会出现警示音，很烦人，设置为不发出声音：

```lisp
(setq ring-bell-function 'ignore)
```
高亮光标所在行：

```lisp
(global-hl-line-mode 1)
```

## 参考
* [通俗org-mode笔记](https://www.yuque.com/idelem/tools/ysxn08)