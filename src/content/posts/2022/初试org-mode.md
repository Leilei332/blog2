---
title: 初试org-mode
published: 2022-04-23
updated: 2022-05-18
slug: tw2022-org-mode-try
tags: 
- Tiddlywiki 2022归档
- 软件
- Emacs
- org-mode
---


org-mode是Emacs自带的一个插件，可以进行任务管理。在网上看了介绍发现是一个基于纯文本任务管理，还挺有趣的。

## 安装
首先安装emacs:

```sh
sudo apt install emacs
```
默认emacs很简陋，所以安装spacemacs,覆盖默认配置文件：

```sh
git clone https://github.com/syl20bnr/spacemacs ~/.emacs.d
git clone https://github.com/syl20bnr/spacemacs %USERPROFILE%/AppData/Roaming/.emacs.d #Windows
```
spacemacs默认使用官网源，比较慢，这里改用镜像源。在`.spacemacs`的`(defun dotspacemacs/user-init ()`加入：

```lisp
(setq configuration-layer-elpa-archives
'(("melpa-cn" . "http://mirrors.tuna.tsinghua.edu.cn/elpa/melpa/")
("org-cn" . "http://mirrors.tuna.tsinghua.edu.cn/elpa/org/")
("gnu-cn" . "http://mirrors.tuna.tsinghua.edu.cn/elpa/gnu/")))
)
```
然后打开Emacs，Spacemacs会开始装一大堆插件，等到初始化完成即可。

完成后把`.spacemacs`的`dotspacemacs-default-font`改成指定字体。这里改成更纱黑体**Sarasa Fixed SC**，大小改成**20**。

## 配置

:::note
以下快捷键<kbd>C</kbd>指代<kbd>Ctrl</knd>，<kbd>M</kbd>指代<kbd>Alt</kbd>，<kbd>S</kbd>指代<kbd>Shift</kbd>
:::

建一个`agenda.el`文件，在`.spacemacs`的`(defun dotspacemacs/user-init ()`加入：

```lisp
(load-file "~/agenda.el")
```
在`agenda.el`文件里加入配置：

```lisp
(setq org-agenda-files '("/media/leilei/Data/Notes/org-mode"))
(global-set-key (kbd "C-c a") 'org-agenda) 
(setq org-default-notes-file "/media/leilei/Data/Notes/org-mode/todo.org")
(global-set-key (kbd "C-c c") 'org-capture)
(setq org-log-done 'time)
```
这里把agenda的位置设为**/media/leilei/Data/Notes/org-mode**，默认的org文件为**/media/leilei/Data/Notes/org-mode/todo.org**，绑定了两个快捷键。这里绑定<kbd>C-c a</kbd>打开agenda页面，<kbd>C-c c</kbd>为新建页面。

此时打开Emacs按<kbd>C-c c</kbd>再按t就能新建一个任务，按<kbd>C-c C-s</kbd>可以添加计划日期，时间，输入按<kbd>C-c a</kbd>再按t能管理任务。

`(setq org-log-done 'time)`可以让任务状态变成<span style="color:green;">DONE</span>的时候添加一个CLOSED属性，记录完成的时间。

### 日期重复
如果想要让计划日期可以重复，将`SCHEDULED:<日期>`改成`SCHEDULED:<日期 +1d>`就可以每天重复，`+1w`则是每周重复。

这种重复默认不会更新时间戳，如果要更新时间戳，可以改成`++1d`
或`.+1d`。`.+1d`会将时间戳更新到完成时间一天后，`++1d`会将时间戳更新到设定时间一天后。

还有一个org-habit插件可以在重复任务上显示热力图，在`agenda.el`里加入：

```lisp
(require 'org-habit)
```

然后在一个任务上输入<kbd>C-c C-x p</kbd>，设置`STYLE:`为`habit`，就可以显示热力图了。注意热力图只会在今天显示，完成就会消失。

### 自定义模板
org-capture默认只有一个选项Task模板，不过这个模板是可以自定义的，参考以下：

```lisp
(setq org-capture-templates
      '(("t" "Task" entry (file+headline org-default-notes-file "Tasks")
         "* TODO %?\n  %i\n  %a")
        ("s" "Study" entry (file+headline org-default-notes-file "Study")
         "* TODO %?\n %i\n %a")
        ))
```

### 配置Diary
Diary是Emacs里一个实用的功能，可以在日历里显示节日，日出日落时间等。org-agenda支持整合Diary，在`agenda.el`里添加

```lisp
(setq org-agenda-include-diary t)
```
可以将org-agenda与Diary整合。

然后配置Diary显示日出，日落时间，首先配置经纬度：

```lisp
(setq calendar-latitude +31.1)
(setq calendar-longitude +121.4)
```
然后添加：

```lisp
(defun diary-sunrise () 
  (let ((dss (diary-sunrise-sunset))) 
    (with-temp-buffer 
      (insert dss) 
      (goto-char (point-min)) 
      (while (re-search-forward " ([^)]*)" nil t) 
    (replace-match "" nil nil)) 
      (goto-char (point-min)) 
      (search-forward ",") 
      (buffer-substring (point-min) (match-beginning 0))))) 
 
(defun diary-sunset () 
  (let ((dss (diary-sunrise-sunset)) 
        start end) 
    (with-temp-buffer 
      (insert dss) 
      (goto-char (point-min)) 
      (while (re-search-forward " ([^)]*)" nil t) 
        (replace-match "" nil nil)) 
      (goto-char (point-min)) 
      (search-forward ", ") 
      (setq start (match-end 0)) 
      (search-forward " at") 
      (setq end (match-beginning 0)) 
      (goto-char start) 
      (capitalize-word 1) 
      (buffer-substring start end))))
```
接下来在`.emacs.d/diary`里添加：

```
%%(diary-sunrise)
%%(diary-sunset)
```

然后打开org-agenda就可以发现可以显示日出日落时间了

### RSS
org-mode自带org-feed.el收取RSS功能，可以把rss收集到一个org文件里。

在`agenda.el`里加入：

```lisp
(setq org-feed-alist
      '(("Sspai"
         "https://sspai.com/feed"
         "D:/Notes/org-mode/feed.org" "少数派")))

```

这里用的是少数派的RSS源。输入<kbd>M-x</kbd>再输入`org-feed-update`，选择订阅源，Emacs就会为订阅源创建org层级，在org文件里就可以查看了。

### 归档
在一个org文件里输入<kbd>C-c C-x C-a</kbd>就可以把org文件的层级归档，内容会移至一个以_archive重新命名的文件里，可以配合RSS使用。

如果不想让归档单独存一个文件，可以在org层级输入<kbd>C-c C-x a</kbd>添加`:ARCHIVED:`属性，此时这个层级显示为灰色，不能按<<.kbd TAB>>展开。

还有一种归档是在当前层级创建一个Archive目录，再将要归档的条目移至Archive条目底下。这个归档方法可以处理已完成的任务，快捷键为<kbd>C-c C-x A</kbd>

### 生成clocktable
在org文件里按<kbd>C-c C-x x<kbd>再选择`clocktable`就可以生成一个分析表格，可以分析当前文件计时统计。如果要包括归档文件，可以将`:scope agenda`改成`:scope agenda-with-archives`。如果只要显示今天，可以添加`:block today`。更新在顶部按<kbd>C-c C-c</kbd>即可。

### 基本操作
org页面

|操作|快捷键|
|-|-|
|折叠层级|<kbd>TAB</kbd>|
|关闭窗口|<kbd>C-x 0</kbd>|
|显示帮助|<kbd>C-h</kbd>|
|打开链接|<kbd>C-c C-o</kbd>|
|org-feed更新|<kbd>C-c C-x g</kbd>|
|计算计时时间|<kbd>C-c C-x C-d</kbd>|
|归档|<kbd>C-c C-x C-a</kbd>|
|添加归档标签|<kbd>C-c C-x a</kbd>|
|设置属性|<kbd>C-c C-x p<kbd>|

agenda页面：

|操作|快捷键|
|-|-|
|添加标签（:tag1:tag2:）|<kbd>C-c C-q</kbd>|
|调整优先级（默认有#A，#B，#C）|<kbd>S UP/DOWN</kbd>|
|标记为完成|<kbd>C-c C-t</kbd>|
|Clock in（开始计时，记录会添加到属性`:LOGBOOK:`）|<kbd>C-c C-x C-i</kbd>|
|Clock out（停止计时）|<kbd>C-c C-x C-o</kbd>|
|添加计划日期|<kbd>C-c C-s</kbd>|
|添加结束日期|<kbd>C-c C-d</kbd>|
|Log mode|<kbd>l</kbd>|
|跳转到今天|<kbd>.</kbd>|
|跳转到日历|<kbd>c</kbd>|
|列视图|<kbd>C-c C-x C-c</kbd>|
|导出|<kbd>C-x C-w</kbd>|

总体来说org-mode的功能很强大，但是还是有不足的地方：移动端功能太少（Orgzly，beorg，mobileorg等）。而且Emacs是要靠键盘操作的，学习门槛很高，需要预先配置。

不过虽然在很多方面不完善，但org-mode作为Emacs的一个插件，在任务管理这个功能上已经是非常完善了，比如热力图功能，计时功能，表格分析功能，甚至是RSS，非常全面。

### 其他[^1]
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

#### Spacemacs配置
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

## 参考
* [使用Emacs做GTD软件](https://zhuanlan.zhihu.com/p/392279466)
* [Org-mode手册](https://brantou.github.io/2017/03/21/just-try/)
* [Org mode beginning at the basics](https://orgmode.org/worg/org-tutorials/org4beginners.html)
* [Org手册](https://emacsist.github.io/emacsist/orgmode/orgmode%E6%89%8B%E5%86%8C%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.html)

[^1]: 此部分内容合并自原文章“org-mode一些配置”（2026.5.23）