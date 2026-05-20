---
title: 使用Firefox代替Edge
published: 2022-04-15
updated: 2022-05-10
slug: tw2022-replace-edge-with-firefox
tags: 
- Tiddlywiki 2022归档
- 日志
- 浏览器
- 软件
---


[img[firefox_HZ4nbGIQv4.png]]

目前Firefox一周用下来感觉还不错，除了有些网站不兼容意外其他方面都很不错（点名晓黑板！）。

!! 为什么要换掉Edge
Edge在Windows上用下来感觉越来越臃肿了，感觉占用越来越大。Chromium最近加了个新功能，在退出后仍然在后台运行，Edge是默认启用的。这大概是我对Edge不满的地方。

最大的问题是Edge在Linux上体验不行，反正我感觉Edge在Linux上没有Linux程序一贯的简洁，所以一开始改用的是Chromium。但又遇到了一个问题：''插件安装''。在国内是无法访问Chrome app store的，而开发者模式的方法安装插件的方式又很麻烦，而且插件目录是不能删的，所以一直用得不顺手。

当时我就准备换了，因为知道Firefox是可以用在线插件的，于是又重新用回了Firefox。重新设计的UI也和Chrome相当了。我用了Firefox ESR版本，Debian上的ESR版本很旧，是78.x版本。

装完后就是整理各种插件，Firefox很早就支持插件折叠菜单功能，右键选“隐藏到折叠菜单”就行了。不过在线插件对于大陆封禁了一些去广告插件，有的去广告插件是可以通过源安装的，Debian源自带uBlock Origin插件，可以通过apt安装。

```
sudo apt install webext-ublock-origin-firefox
```
在其他平台上，也可以在GitHub上下载签名的xpi文件安装。目前的书签导入等基本都没问题，不过内存占用比Chromium高一些。