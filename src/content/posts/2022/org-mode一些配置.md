---
title: org-mode一些配置
published: 2022-06-03
updated: 2022-06-03
slug: tw2022-org-mode-config
tags: 
- Tiddlywiki 2022归档
- 日志
- org-mode
- Emacs
- 软件
---


在日历里高亮节日：

```lisp
(setq calendar-mark-holidays-flag t)
```

之前在org-agenda里显示Diary的方法是这样：

```lisp
(setq org-agenda-include-diary t)
;; diary
;; %%(diary-sunrise)
;; %%(diary-sunset)
```
这样会拖慢org-agenda加载速度，所以推荐使用下面这种在org文件里配置的方法：

```
* Holidays
:PROPERTIES:
:CATEGORY: holiday
:VISIBILITY: folded
:END:
%%(org-calendar-holiday)
* Sun
:PROPERTIES:
:CATEGORY: sun
:VISIBILITY: folded
:END:
%%(diary-sunrise)
%%(diary-sunset)
```
这样可以提升org-agenda的初始化速度。

!! Spacemacs配置
```lisp
(defun dotspacemacs/init ()
(setq-default
;; ...
;; 显示列表
dotspacemacs-startup-lists '((recents . 5)
(agenda . 5)
(todos . 7)
)
;; underwater主题
dotspacemacs-themes '(underwater
spacemacs-dark
spacemacs-light)
;; ...
;; 启动时全屏
dotspacemacs-maximized-at-startup t
))
```