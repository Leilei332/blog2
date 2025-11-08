---
title: 老笔记本上Linux使用体验
published: 2023-08-18
updated: 2023-10-12
tags: 
- Linux
---


> 此文尽量保证在Linux系统上写成

在准备给一个老笔记本装一个[[Linux]]系统时正好[Debian 12发布了](https://www.debian.org/News/2023/20230610)，目前在7月22日更新之后是Debian 12.1版本。所以就讲一下老笔记本上的Debian 12使用体验。

## Debian 12目前遇到的问题
由于是刚刚出来的正式版，所以目前使用过程中还是有很多问题。
* 驱动不稳定，有概率启动登录之后只有触屏可以使用。键盘，触控版不能用。
* 默认设置默认输入法为ibus输入法，没有预装fcitx5输入法。但是KDE桌面需要fcitx5输入法。这个比较好解决，安装fcitx5再运行`im-config`设置一下即可。
* 自带的包`raspi-firmware`会导致Linux内核无法升级，需执行`sudo dpkg --purge raspi-firmware`清除。

## 笔记本信息
这个笔记本比较老，所以里面的硬件完全跟不上现在的主流配置。内存大约4G，所以在安装时分了swap分区。

虽然据说Linux对老硬件的支持比较好，但事实上这也与发型版自带的桌面环境也有关。Gnome和KDE两个桌面环境都比较大，都需要比较大的内存。在这个老的笔记本上运行KDE内存基本都是超过一半的，所以如果笔记本硬件实在不行Linux也救不了，老版的Windows反而更适合。

## 体验
虽然Linux在“对用户友好这个方面”这个方面做得没有Windows和macOS好，但是目前已经得到了很大的改善。新版的KDE和Debian也在用户体验方面提升了很多。

目前Debian 12改善的地方有：
* [默认自带“不自由”的硬件驱动](https://www.debian.org/releases/bookworm/amd64/release-notes/ch-information.en.html#non-free-split)，这些驱动都移至了*non-free-firmware*仓库
* KDE版本自带`xdg-desktop-portal-kde`包

由于Linux桌面环境的分裂，Linux上的应用程序有很多不统一的用户体验，其中有一个问题就是文件选择器的不同。即使是KDE上的应用程序，GTK/Electron应用也会默认使用~~垃圾的~~Nautilus文件选择器，解决办法是安装*xdg-desktop-portal-kde*这个包，并在`/etc/security/pam_env.conf`加入：

```
GTK_USE_PORTAL DEFAULT=1
```

### 触屏体验
由于这个笔记本是支持触屏的，所以说一下触屏在Linux上的体验。

虽然Gnome桌面环境的布局适合触屏操作，但是触屏在上面的体验并没有那么好，大概和KDE一样。目前Debian 12的KDE相对于Debian 11的KDE也有了一些改善，比如新版KDE可以长按桌面进入编辑模式，Dolphin新增选择模式等。

KDE上对触屏的支持比较一般，不支持通过长按来呼出右键菜单[^1]，文件管理器Dolphin支持了长按手势，但是无法灵敏地呼出右键菜单。不过里面有些应用对触屏的支持还是超过了预期，目前以下种类的应用对触屏的支持比较好：

* 浏览器：Chrome,Firefox
* 基于GTK/Qt的应用：KDE内置的文档查看器Okular，[uGet](https://ugetdm.com)等
* Electron应用：非常多，比如VSCode,QQ,百度网盘等。

其中Firefox默认不支持触屏操作，需要打开about:config页面设置`dom.w3c_touch_events.enables`为1。然后在`/etc/security/pam_env.conf`加入：

```
MOZ_USE_XINPUT2 DEFAULT=1
```

### 图形界面基本体验
Debian 12上的KDE是默认选择Wayland的，体验后发现KDE目前对Wayland的支持还挺不错。而且在老笔记本上体验发现Wayland上的KDE比X11上的KDE更加流畅。反而是X11上的KDE桌面经常会在不知道做了什么操作就会崩溃，只能手动运行`plasmashell`命令。**2023年了，X11这个老古董已经超过10年没有更新了，真的没必要太依赖这种旧的东西了。**

不过Wayland上面又有一个坑——无法使用输入法，需要在`/etc/security/pam_env.conf`加入：

```
GTK_IM_MODULE DEFAULT=fcitx5
QT_IM_MODULE DEFAULT=fcitx5
XMODIFIERS DEFAULT=@im=fcitx5
```

还有一个坑是KDE系应用内置的字体查看器失效，用kfontview打开字体也会提示错误，详见[此链接](https://bugs.kde.org/show_bug.cgi?id=439470)。

另外，在Linux上使用Papirus Icon Pack和Materia KDE主题之后KDE出现了明显的卡顿，使用默认的主题就没有这个问题。有可能是Kvantum消耗系统资源的原因。

### 软件生态
这在Linux上是一个比较大的问题，不过目前Linux在这方面改善了许多。目前常用的支持Linux的软件有QQ[^2],百度网盘等。

其中尤其是开源软件对Linux的支持比较好，像[[Emacs]]，GIMP这些在软件包仓库就有。

另外很多人认为Linux上的游戏很少，其实Linux平台上的游戏比想象中的多，Steam就有Linux版本。支持Linux的游戏包括：

* 基于起源引擎的游戏：传送门，传送门2，半条命2，CSGO，GMOD等
* P社游戏：城市：天际线，[[钢铁雄心4]],维多利亚3等
* 其他3D游戏：Minecraft，
* 其他游戏：迷你地铁，Limbo，Undertale，泰拉瑞亚，

[^1]: 这一点Gnome做得比较好，在Gnome的辅助功能中可以启用长按触屏呼出右键菜单

[^2]: 在使用Electron架构之后Linux上的QQ已经实现了比较完整的功能。
