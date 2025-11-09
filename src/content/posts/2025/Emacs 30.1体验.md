---
title: Emacs 30.1体验
published: 2025-03-02
updated: 2025-04-18
tags: 
- Emacs
abbrlink: emacs-301
---


Emacs 30.1已经正式发布

## 配置更新

<!-- TEASER_END -->

### package.el快速启动
之前一直没注意到package.el的＂快速启动＂功能。这个功能很早就有了，可以通过如下方式启用：

```emacs-lisp
(setq package-quickstart t)
```

启用后可以通过`package-quickstart-refresh`生成一个`package-quickstart.elc`文件。 

### use-package配置
改两个设置就行。

```emacs-lisp
(setq use-package-always-defer t)
(setq use-package-expand-minimally t)
```

另外，推荐在配置中尽量避免`:config`、`:init`和`:preface`等关键字，而改用`:bind`、`:hook`、`:custom`等，使use-package能发挥autoload功能。

### 启用内置which-key-mode
which-key-mode在30.1已被eMacs内置。用use-package配置：

```emacs-lisp
(use-package which-key
  :ensure t
  :pin melpa-stable
  :init
  (which-key-mode 1))
```

### 启用completion-preview-mode
又是一个新加入eMacs的包，可以在elisp-mode等与编程相关的mode中预览补全内容，并用tab键补全。

```emacs-lisp
(use-package completion-preview
  :hook (prog-mode . completion-preview-mode))
```

### Evil配置
Evil还是比较卡启动速度的，所以在`use-package`设置了2秒后加载。

```emacs-lisp
(use-package evil
  :pin melpa-stable
  :defer 2 ; 2秒后加载
  :ensure t
  :config
  (evil-mode 1)
  (evil-set-initial-state 'read-only-mode 'motion)
  (evil-set-initial-state 'dashboard-mode 'motion)
  (evil-set-initial-state 'vc-dir-mode 'motion))
```

为了能在org-mode中使用evil,还安装了evil-org这个包：

```emacs-lisp
(use-package evil-org
  :ensure t
  :autoload evil-org-mode
  :after (evil org)
  :hook (org-mode . evil-org-mode)
  :config
  (evil-org-set-key-theme '(navigation insert textobjects additional calendar)))
```

## 新增的包
### Markdown

目前开始用Emacs写Markdown了，

```emacs-lisp
(use-package markdown-mode
  :ensure t
  :pin melpa-stable
  :custom (markdown-fontify-code-blocks-natively t))
; 附加的edit-indirect包，支持类似org-mode编辑代码块的功能
(use-package edit-indirect
  :ensure t
  :after markdown-mode)
```

### adoc-mode
写Asciidoc，由于功能简陋，不太常用。

```emacs-lisp
(use-package adoc-mode
  :ensure t)
```
