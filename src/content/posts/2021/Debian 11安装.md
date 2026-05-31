---
title: Debian 11安装
published: 2021-09-29
updated: 2021-11-12
slug: j2021-debian-11
tags: 
- Joplin 2021补档
- Linux
---


看来已经两个月没写了，最近8月14日新出了Debian 11（其实不是新出，testing早就有了)，据说这个发行版比Ubuntu稳定，所以决定去使（尝）用（鲜），这里记一下安装的过程和后续配置。
## 1.下载iso

iso有很多版本，不过默认的版本很坑，下的是netinst版本，很多包要网上下载，而再仔细找才能找到DVD大文件版本。

这两个版本的安装界面用的是安装器界面，选项很多，但也造成了安装过程繁琐，而且安装后会出现很多问题（如sudoers问题），而另外的live版的安装器相比比较简洁，而且坑更少，因此不建议使用此版本。

> live只支持amd64和i386的cpu（即64位和32位）

不过Debian默认没有附带驱动，所以里面提供了带驱动的nonfree版本的连接，三个版本都有，这里推荐使用nonfree版本，如果条件允许也可以下载固件包，安装完整系统后再安装。

> 注意：较老的Debian版本的驱动过老（缺失），如果电脑较新不要使用老版本！

在[Debian.org](https://debian.org)点下载，在下面选择“含有非自由固件”，点击*版本号*-live+nonfree，*CPU版本*，iso-hybird，里面提供了很多桌面，如Gnome，KDE，Xfce等，这里选择Gnome桌面版本。

## 2.写入U盘

Debian live比较特殊，可能是使用了特殊的文件系统，在Windows下写入有问题，在Linux下无问题（使用Etcher），如果没有Linux电脑，只能用虚拟机将U盘连接到Linux虚拟机的方法写入了，这里不细讲了。

另外，ventoy无法启动live系统，会卡在grub菜单。

## 3.安装

从U盘启动，进入桌面。

Gnome版本需要点击左上角的“活动”，然后点击左边的Dock的最上面的安装器。

其他的桌面环境，如果带有桌面，桌面应有安装器的快捷方式。

打开后选择语言，一直到分区这里，BIOS只需分一个**/**分区，而UEFI需要多分一个**FAT32**文件系统的**/boot/efi**分区，然后设置用户名和密码就可以等待了。

## 4.配置

Debian默认捆绑了一些软件，处理方法：

- Libreoffice:

  ```sh
  sudo apt remove libreoffice-common
  ```

- 过老的软件:

  ```sh
  sudo apt remove hdate-applet kasumi mlterm-common xiterm+thai goldendict 
  ```

- 输入法

  >Gnome下默认使用ibus输入法，其他桌面默认使用fcitx

  Debian 11自带了ibus-m17n输入法（日语也自带ibus-mozc），但里面没除了注音输入法没几个能用的，所以安装ibus-pinyin：

  ```
  sudo apt install ibus-pinyin #ibus-rime
  ```

  当然也可以安装Rime输入法，但是因为有着诡异的操作方式，这里不推荐

- 多余输入法

  - uim

    ```sh
    sudo apt remove uim* #Gnome使用ibus输入法可以添加fcitx*，其他桌面按需卸载
    sudo apt autoremove
    ```

- 游戏（Gnome）

  ```sh
  sudo apt remove aisleriot five-or-more four-in-a-row gnome-2048 gnome-chess gnome-klotski gnome-mahjongg gnome-mines gnome-nibbles gnome-robots gnome-sudoku gnome-taquin gnome-tetravex iagno lightsoff quadrapassel hitori tali #按需卸载
  ```
  

主题：~~其实没什么必要，不过也列一些之前用过的主题~~

现在已经用上Materia主题了，截图：


```shell
sudo apt install adapta-gtk-theme materia-gtk-theme papirus-icon-theme paper-icon-theme
```

自己去"优化"设置即可

添加flatpak：

原来只有零星软件的Debian换了flathub后总算可以用了：

```
sudo apt install flatpak
```

### 建立Outlook同步

如果你使用Outlook邮箱，就可以通过Gnome设置登录在线账户同步邮箱了，而下面的Exchange邮箱则可以同步日历，只要将服务器设置为**outlook.office365.com**，用户名设置为邮箱，其他照样填就行。

同步之后，我发现，**连Microsoft To Do的待办事项都能同步！**

当然，首先要下载安装evolution，evolution-ews和gnome-todo，其中evolution和gnome-todo应为预装应用

```sh
sudo apt install evolution-ews #evolution gnome-todo
```

然后在gnome-todo和gnome-calendar就可以看到日历和待办事项了

## 5.最后