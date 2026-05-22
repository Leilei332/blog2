---
title: 给Debian换主题
published: 2022-07-18
updated: 2022-07-24
slug: tw2022-change-debian-theme
tags: 
- Tiddlywiki 2022归档
- Linux
---


Debian默认带了很多不错的主题，并且都很齐全，有Grub主题，Plymouth主题，登录界面主题等。

## 设置Plymouth主题
Debian进入系统的加载界面的主题是可以换的，可以用Plymouth实现。

首先输入`sudo /usr/sbin/plymouth-set-default-theme -l`列出可用的主题

接下来如果要换一个Moonlight主题，在终端输以下：

```bash
sudo /usr/sbin/plymouth-set-default-theme moonlight
sudo update-initramfs -u
```

## 设置grub和桌面主题
这个可以用内置工具`update-alternatives`实现

在终端输入：

```bash
sudo update-alternatives --config desktop-theme
```
在列出的路径里选择一项，比如Moonlight，输入对应的数字就行了。最后再更新一下Grub：

```bash
sudo update-grub
```
重启就能看到效果了。

## 参考

* [plymouth - Debian Wiki](https://wiki.debian.org/plymouth)
