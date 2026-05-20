---
title: Linux发行版体验总结
published: 2021-10-03
updated: 2021-11-12
tags: 
- 日志 2021
- Linux
---


在众多Linux发行版中，我体验了大概这么多发行版：

* Ubuntu
** Kubuntu
* Fedora（仅虚拟机）
* Debian
* Manjaro

目前正在用的是[[Debian|Debian 11安装]]，最新版本11 bulleye

!! Ubuntu
Ubuntu是自己还是一个Linux小白时用的，当时第一次是在Virtualbox里安装Ubuntu 18.04，后来又体验了类似的Linux Mint发行版，也在里面运行了之前写的Python Tkinter程序，直到后面才开始第一次在电脑上安装

不过那时Ubuntu的桌面很不稳定，记得在所有应用打开应用文件夹崩了一下，锁屏放音乐时突然崩了，到了后面直接不能启动，所以后面我用了Kubuntu代替

<<<
还有一个问题是不稳定，除了桌面，软件的版本经常不统一，这也就算了，还有一个原因是内核随便升级，要知道Debian滚动发行模式的testing和sid也要添加backdrops才能升级内核，导致容易崩溃
<<<
!!! Kubuntu
Kubuntu相对Ubuntu稳定了很多，安装也更快，KDE也还算好用，日常使用也没什么问题

''但是……''

Kde目前对hdpi的支持还是较差，我首先把缩放调为150%，但某些图标还是糊了，第二次用把缩放调为200%，图标不糊了，但某些java应用显示不正常。

还有一个奇怪的bug，每次休眠再唤醒的时候会花屏。剩下的问题都是Ubuntu的问题了。

反正这是用的最久的一个发行版了，Ubuntu后面在用，Manjaro用完后也在用

!! Manjaro
这是在弃用Kubuntu后用的一个发行版，当时听说了Arch Linux发行版，但在虚拟机没有安装成功，所以在实机安装用的是Manjaro图形安装双系统。

由于我当时用惯了Kde，所以我使用了Gnome版本，一开始自带的Gnome 3.38的版本也很稳定，所有的软件都可以用pacman安装，还算好用，除了Gnome ''Wayland''下的OBS Studio和f.lux软件不能用的这些Gnome本身的问题。

其中因为没有删前面的Kubuntu系统，在第二次操作中移动的''/boot/efi''分区而导致Manjaro无法启动，只好重装Manjaro，后面就没怎么做死了。

导致我放弃Manjaro的是它的滚动更新的机制，因为滚动更新，所以Gnome升级到了40.0版本，而且非常不稳定，切换窗口都会崩溃，只能注销，所以又换回了Kubuntu。

当时Kubuntu一直在用，然后Debian 11就出了，当时有点想升级，Kubuntu也因为内核升级的原因出了问题。当时在知乎上看到了Debian与Ubuntu的对比，也知道了nonfree镜像版本（见[[Debian 11安装]])，所以安装了。

!! Debian
最后一个也是目前在用的发行版，目前用下来还是很稳定的，因为Debian的Stable分支用的是固定的软件版本，每个大版本都有自己的仓库，目前对Debian 9的oldoldstable也在维护。

目前唯一的问题是对硬件支持较差，Debian 10-live nonfree版本在我的电脑上不能进入图形界面，不过Debian 11驱动又跟上来了，体验还不错，Gnome 3.38原生版本也很好看。

目前的Linux发行版体验就是这样，后面会单独加。