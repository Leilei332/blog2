---
title: 搞定kodi-vfs-rar问题
published: 2021-09-29
updated: 2021-09-29
tags: 
- 补档
---


想装一个bilibili弹幕插件，但是会跳出来一个“无法满足依赖vfs.rar”的问题，只要装一个包就可以了。但Ubuntu的基础源没有这个包，所以先添加PPA源：
```
sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt-get update
sudo apt-get install kodi-vfs-rar
```
但这里下载的vfs.rar版本过新，只能兼容19.x版本的kodi，而高版本的kodi又不兼容弹幕插件，所以只能改一下文件，使用老的vfs.rar版本。

编辑`/etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-focal.list`：
```
sudo nvim /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-focal.list
```
将`focal`换成`xenial`，再`sudo apt update`。

这时安装就不会出现问题了