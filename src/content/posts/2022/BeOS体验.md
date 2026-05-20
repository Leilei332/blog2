---
title: BeOS体验
published: 2022-01-14
updated: 2022-01-24
tags: 
- 日志
- OS
---


[img[belogo.jpg]]

! 🌕
把最近的文章整理的一下，把很多已经不准备写的内容都删掉了，而且把[[暂定]]加了删除的选项，加了一个RevealWidget，给[[Home]]也加了一个timeline。

上面都是最近对TiddlyWiki的改造，BeOS去年就体验过一次，之前有写文章的想法，但现在才开始。下面开始正题：

!! 历史
<font color="#0000FF"><u>B</u></font><font color="FF0000"><u>e</u></font>
OS来源于<font color="#0000FF"><u>B</u></font><font color="FF0000"><u>e</u></font>公司，这个公司好像是从苹果公司分裂出来的，不过这个公司的名字到很有创意，<font color="#0000FF"><u>B</u></font><font color="FF0000"><u>e</u></font>就是英语中的“是”的意思。商标也很富有特色，有着鲜明的<font color="#0000FF">蓝</font><font color="FF0000">红</font>配色，这样的设计在BeOS也有体验。

根据介绍，BeOS是对多媒体有着强大支持的，比如说3D。最后苹果公司准备收购Be公司，但由于钱不够的问题被Be公司拒绝，所以最后苹果收购的是乔布斯的NeXT Inc，BeOS就此停止开发。继任者则是开源的Haiku OS，目前好像出Beta 3了。

!! 安装
镜像可以在[[winworld|https://winworldpc.com]]找到，下载好x86镜像，然后打开86Box进行相关设置即可，一般不太特殊的ROM都可以兼容BeOS，BeOS 5甚至还原生兼容VGA，可以在VirtualBox上安装。

这里选的镜像是BeOS 4.0，注意BeOS 5.0 Pro是没有cue格式的镜像的！

启动之后直接傻瓜式安装，然后硬盘要自己创建分区，在Options里选择Setup Partitions分区即可。接下来语言有英语和日本语，按需求选就行了。

!! 体验
BeOS的某些体验比较神奇，比如说，在浏览器打开一个网站时（此时没连接到网络），提示的信息是：

<<<
Serious error.

The sit, vanished into dust.

Screen. Mind. Both are blank.
<<<
虽然之前在网上看到过BeOS报错日志就像写诗一样，不过看到这样的情况还是很神奇，类似的还有：

<<<
Ephemeral site.

I'm the Blue Screen of Death.

No one hears your screams.
<<<
这样的例子有很多，只要重试就会换一个。不过内置的浏览器还不支持https加密连接，只会提示去官网下，可能是版本过老的原因罢……

当然，其他方面的体验肯定比同时代Windows 98好很多。相比于Windows 98冷冰冰的配色，BeOS配色鲜明，有着macOS般的界面。里面还自带了BeIDE，BeMail等应用。系统应用也很不错，里面的监视CPU占用的工具甚至把CPU信息变成了CPU图标。虽然UI分辨率不高，但在鲜明的颜色下就像像素艺术一样。

不过最值得看的还是里面的终端应用，在这个应用里是支持Unix命令的，所有的命令都在`/boot/beos/bin`里面，`beep`命令可以在装了声卡的电脑里发出“嘀”的声音，还有一个奇葩的应用则是`/boot/beos/bin/[`，是一个链接到`/boot/beos/bin/test`的链接，执行不输出任何内容。

然后就是BeOS强大的3D了，BeOS 4.0自带很多Demo，3d的Demo特别多，里面似乎用的是GL（有一个Demo叫GLTeapot）。在128MB的内存下，BeOS居然还能运行一个比较复杂的3D飞机应用，可以说是非常先进了。

!! <font color="#0000FF">B</font><font color="FF0000">e</font>Box
说到BeOS就要说到BeBox，这是Be公司的电脑，看上去是一个给普通用户的电脑，不过Be公司的CEO认为这是高端产品，就像乔布斯看NeXTCube一样。这个产品下场也和NeXTSTEP一样，卖得不好。

!! 参考
[[Apple Wiki|https://apple.fandom.com/wiki/BeOS]]