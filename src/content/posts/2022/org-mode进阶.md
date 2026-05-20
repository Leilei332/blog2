---
title: org-mode进阶
published: 2022-06-25
updated: 2022-08-16
slug: tw2022-org-mode-ext
tags: 
- Tiddlywiki 2022归档
- 日志
- 暂定
- org-mode
- Emacs
---


之前写过一个[[初试org-mode]]，里面介绍了一些基本的org-mode功能。

{{初试org-mode||$:/Scrollview}}

最近研究了一下[[org-mode]]，发现里面还是有很多实用的功能。

之前一直用spacemacs，后来是spacemacs-base，现在换成原生Emacs了，自己配置初始化文件。

<details><summary>初始化文件</summary>
<$codeblock code={{.emacs}} language="lisp" />
</details>

> 之前推荐[[Trilium]]的[[idelem|https://yuque.com/idelem]]目前放弃Trilium转用org-mode了

!! Emacs基本操作
推荐开启`menu-bar-mode`了解对应按键。

|键|命令|h
|<kbd>C-x 0</kbd>|关闭buffer|
|<kbd>C-x k</kbd>|杀死buffer（让buffer完全消失）|
|<kbd>C-x b</kbd>|切换buffer|
|<kbd>C-x h</kbd>|全选|
|<kbd>C-x u</kbd>|撤销|
|<kbd>C-y</kbd>|粘贴|
|<kbd>M-w</kbd>|复制|
|<kbd>M-x</kbd>|运行命令|

!! 主题
~~目前推荐使用[[Gotham|https://emacsthemes.com/themes/gotham-theme.html]]，富有科技感的主题。~~已经换到[[doom-themes|https://github.com/doomemacs/themes]]了，现在在用//doom-material-dark//主题，基于//gruvbox//改的。

!! org-capture
[[文档|https://orgmode.org/manual/Capture.html]]

一开始并没有深入使用org-capture，在深入了解之后发现这个记录功能非常强大。

```lisp
(setq org-capture-templates
      '(("t" "Task" entry (file+headline org-default-notes-file "Tasks")
         "* TODO %?\n %i\n")
        ("s" "Study" entry (file+headline org-default-notes-file "Study")
         "* TODO %? %^G\n%u %i\n")
        ("o" "Other" entry (file+headline org-default-notes-file "Others")
         "* TODO %?\n%u %i\n")
	("r" "Record")
        ("rr" "Record" entry (file+datetree "record.org")
         "* %? :record:\n%T\n")
	("rc" "Record Clock" entry (file+datetree "record.org")
	 "* %? :record:\n%T" :clock-in t :clock-keep t)
        ("e" "Event" entry (file+datetree "record.org")
         "* %? :event:\n%^T\n")
	("j" "Journal" plain (file+datetree "journal.org")
	 "%U\n%?" :unnarrowed t)
	("o" "Others")
	("ot" "Ted" entry (file+olp org-default-notes-file "Others" "Ted")
	 "* TODO %?\n%u")
	("op" "Podcast" entry (file+olp org-default-notes-file "Others" "Podcast")
	 "* TODO %?\n%u")
	("ob" "Book" entry (file+headline org-default-notes-file "Book")
	 "* TODO %?\n%u")
	))
```
org-capture自带一个//datetree//功能，可以在org文件里生成一个通过日期分类的大纲，只要把前面设为`file+datetree`即可。

我把//datetree//专门放在了一个record.org文件里。里面都记录了一个时间戳，可以在org-agenda里显示记录的内容。普通的记录用`%T`可以自动添加时间戳。对于事件，用`%^T`，可以弹出一个时间选择器。而用`%^G`（或`%^g`）可以弹出一个标签选择器（支持<kbd>TAB</kbd>补全）。

一些特殊标识符：

|表示|描述|h
|`%t`|现在日期|
|`%u`|现在日期（非活动）|
|`%T`（或`%U`）|现在日期和时间|
|`%?`|光标停留位置|
|`%x`|剪贴板内容|

!!! 分组
如果给每个项目都只定一个键那么就会很混乱，所以org-capture自带了一个分组的功能，比如要按两下<kbd>r</kbd>键记录，按<kbd>rc</kbd>记录另一个，可以在前面添加一个`("r" "Record")`进行分组。

```
	("r" "Record")
        ("rr" "Record" entry (file+datetree "record.org")
         "* %? :record:\n%T\n")
	("rc" "Record Clock" entry (file+datetree "record.org")
	 "* %? :record:\n%T" :clock-in t :clock-keep t)
```

!! 快捷org-agenda命令
之前一直使用复杂的<kbd>C-c C-t</kbd>这种复杂的命令，其实在org-agenda里有很多一键触发的快捷指令。

|键|Evil键|命令|h
|<kbd>b</kbd>|<kbd>[[</kbd>|向前|
|<kbd>f</kbd>|<kbd>]]</kbd>|向后|
|<kbd>d</kbd>|<kbd>gDd</kbd>|日视图|
|<kbd>e</kbd>|<kbd>ce</kbd>|设定|
|<kbd>w</kbd>|<kbd>gDw</kbd>|周视图|
| <kbd>t</kbd> |<|切换TODO|
|<kbd>l</kbd>|<kbd>gDl</kbd>|Log mode|
| <kbd>r</kbd> |<|刷新|
|<kbd>R</kbd>|<kbd>cr</kbd>|Clocktable mode|
|<kbd>:</kbd>|<kbd>ct</kbd>|设置标签|
| <kbd>.</kbd> |<|跳转至今天|
| <kbd>o</kbd> |<|最大化（同<kbd>C-x 1</kbd>）|
| <kbd>I</kbd> |<|开始计时|
| <kbd>O</kbd> |<|停止计时|
|<kbd>X</kbd>|<kbd>cc</kbd>|取消计时|
|<kbd>J</kbd>|<kbd>cg</kbd>|跳转至正在计时的任务|
|<kbd>S</kbd>|<kbd>C-x C-s</kbd>|保存所有org文件|
|<kbd>/</kbd>|<kbd>st</kbd>|筛选（按标签或`CATEGOTY`）|
|<kbd>|</kbd>|<kbd>S</kbd>|去除筛选|
|<kbd>a</kbd>|<kbd>da</kbd>|归档|
|<kbd>c</kbd>|<kbd>ac</kbd>|跳转至日历|
|<kbd>z</kbd>|<kbd>a</kbd>|添加笔记|
| <kbd>m</kbd> |<|标记|
|<kbd>B</kbd>|<kbd>x</kbd>|对标记的部分批量操作|

按<kbd>v</kbd>(Evil:<kbd>gD</kbd>)键可以切换查看模式。

|键|命令|h
|<kbd>v t</kbd>|两周视图|
|<kbd>v m</kbd>|月视图|
|<kbd>v y</kbd>|年视图|
|<kbd>v a</kbd>|包括已归档|
|<kbd>v c</kbd>|Clockcheck视图|
|<kbd>v E</kbd>|查看条目内部文字|
|<kbd>v [</kbd>|包括非活动时间戳|

!! 分屏
[[Emacs]]原生支持分屏，可以让很多窗口显示在一起。

|键|命令|h
|<kbd>C-x 0</kbd>|关闭窗口|
|<kbd>C-x 1</kbd>|最大化（关闭其他窗口）|
|<kbd>C-x 2</kbd>|在下面分屏|
|<kbd>C-x 3</kbd>|在左侧分屏|

!! org-attach
org-attach可以给org文件里的标题添加附件，默认按<kbd>C-c C-a</kbd>就可以激活。

激活之后按<kbd>a</kbd>输入一个路径，这个标题就会添加上一个`ID`属性，文件会移动到org目录的data文件夹里，打开按<kbd>C-c C-a o</kbd>就行了。

<kbd>C-c C-a s</kbd>命令可以给标题设置一个路径

!! 标签
Org-mode可以给标签设置快捷键，这样不用在设置标签时按<kbd>TAB</kbd>补全，只要在设置`org-tag-alist`里把标签改成`("tag" . ?t)`，这样在输入时就可以直接按<kbd>t</kbd>来设置标签了。

注意如果使用`(:startgroup)`和`(:endgroup)`中的标签是只能在其中选择一个，标签选择界面显示为花括号。如果要临时选择多个标签，按<kbd>!</kbd>临时关闭分组。

```lisp
(setq org-tag-persistent-alist '((:startgroup)
                      ("eng")
                      ("math")
                      ("chs")
                      ("phy")
		      ("che")
		      ("his")
                      (:endgroup)
                      ("games")
                      ("药" . ?y)
                      ("podcast")
                      ("video")
		      ("book")
		      ("sports")
                      ("record")
                      ("event")
		      ("emacs")
		      ("tiddlywiki")
		      (:startgroup)
		      ("video")
		      (:grouptags)
		      ("ted")
		      ("bilibili")
		      ("movie")
		      (:endgroup)))
```

设置标签的命令：

|键|命令|h
|<kbd>!</kbd>|关闭分组|
|<kbd>TAB</kbd>|用原标签输入添加标签|
|<kbd>SPC</kbd>|清除所有标签|

最后是一个标签缩进的问题，默认标签距离标题很远。如果想要标签距离标题一个空格，可以添加：

```lisp
(setq org-tags-column 0)
```

!! org内置实用模块
!!! org-mouse
让org-mode有鼠标支持，比如可以点击打开或折叠标题。

!!! org-habit
可以显示重复任务为热力图。

!! org-contrib
org-contrib是一个org-mode第三方插件集合，里面有很多实用插件

!!! org-expiry
org-expiry可以用`EXPIRY`属性自动添加`:ARCHIVE:`标签，首先用<kbd>M-x</kbd>执行//org-expiry-insert-expiry//添加一个属性。到后面执行//org-expiry-process-entries//就可以了。

!!! org-sudoku
可以在org-mode里自动生成数独表格！

{{$:/sudoku}}

!! 自定义归档

```lisp
;; Archive
(setq org-archive-location "D:/Notes/org-mode/archive.org::* From %s")
```

!! @@.pub-under-const 其他配置@@
```lisp
()
```

!! 参考
* [[Org manual|https://orgmode.org/manual/]]
