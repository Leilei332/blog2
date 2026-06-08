---
date: "\\<2022-09-30 周五 19:17\\>"
published: 2022-09-30
description: Emacs在安卓上的体验
title: Termux上的Emacs
tags:
- Hugo 2023归档
- org-mode
- Emacs
- Android
slug: h2023-emacs-on-android
---

目前在移动设备上org-mode的解决方案有[Orgzly](https://orgzly.com)，[Organice](https://organice.200ok.ch/)，Beorg等，其中Organice的支持是最好的，但是完美的org-mode支持目前只有Emacs。因为org-mode非常复杂，单单任务计划，标记就有一大堆东西，所以我又重拾了在Android上运行Linux程序的方案： **Termux**

# 安装

Termux在2022年重拾了对Android 5的支持，不过只能通过Github Actions里生成的文件来安装，选择 `apt-android-5` 即可。

安装好apk，等待Termux初始化完成后，就可以用终端了。输入以下代码：

``` shell
apt install emacs
```

# 同步org文件

一开始我用的是Orgzly，所以我使用了Webdav同步。在Linux上虽然有支持Webdav的工具rclone，但是同步操作太麻烦，所以我现在使用Git来代替。而且Emacs内置的 `vc-git` 默认对Git有很好的支持。

为了避免每次提交需要输入密码，我用了GitLab的令牌功能。在[GitLab的令牌页面](https://gitlab.com/-/profile/personal_access_tokens)可以生成一个令牌。

然后将URL改成 `https://outh2:令牌@gitlab.com` 就行了。

## VC的使用

按 `C-x v d` 就可以查看所有文件的状态，提交文件先在要提交的目录或文件上按 `m` 标记[^1]，再用 `C-x v v` 提交文件。最后按 `P` 推送文件即可。

# 和organice同步

在organice里输入GitLab的URL，然后会跳转到GitLab的授权页面，同意授权即可。

然后在其他设备上拉取可以在VC的页面上按 `+` ，如果在终端可以输入下面这个：

``` shell
git pull
```

# 问题

目前organice和Termux上的Emacs基本没大问题，不过有几个问题很影响体验：

1.  **语言** organice和Termux的时间戳都是英文。时间戳的格式影响不大，不过Termux上的datetree功能也是英文，与电脑上的中文冲突，所以安卓上的org-capture功能废了一半。[^2]
2.  **速度** 即使不自动加载Org Agenda，启动速度还是很慢。因为老安卓手机的性能不好。
3.  **版本** 由于Termux对于Android 5的支持只有老的源，所以自带的Emacs版本比较低，Org-mode还是8.x版本。

[^1]: 一般在 `\.` 上按m就可以提交所有文件

[^2]: 这个是因为Termux不支持locale语言包
