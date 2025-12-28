---
title: 通过WebDAV方式保存Tiddlywiki
published: 2023-05-07
updated: 2025-12-28
tags: 
- Tiddlywiki
abbrlink: tiddlywiki-save-webdav
---


:::note
2025年11月9日更新：增加[Copyparty](https://github.com/9001/copyparty)这个WebDAV工具（虽然目前已不用WebDAV保存方式）
:::

Tiddlywiki是一个很不错的工具，但唯一的一个麻烦点就是保存起来麻烦。

在[Tiddlywiki官网]上介绍了以下保存方式

* 下载保存
* 客户端保存
* Git保存（GitHub，GitLab，Gitea）
* [TiddlyHost]保存

其中下载保存是默认的保存方式，由于太麻烦，所以不介绍。

## 客户端保存
Tiddlywiki有一个官方的客户端[TiddlyDesktop]，这也是我第一次用Tiddlywiki时的保存方式，支持三大桌面操作系统。后来又换成了[Timimi]，一个通过浏览器插件和本地服务端实现的Tiddlywiki本地保存方法。

但对于移动端来说本地保存就有些困难了，在Android上的支持本地保存的App有[Tiddldroid]，在iOS上的App只有[Quine]，而且是收费¥38的应用。这条路在iOS上就废了。

## Git保存
这也是Tiddlywiki内置的一种保存方式，Tiddlywiki默认就支持保存在[GitHub]，[GitLab]，和[Gitea]上。由于Git服务器是方便访问的，所以这个方法可以在iOS上使用。

在iOS上的Git应用有[Working Copy](https://workingcopy.app/)，可以将Git仓库克隆到本地。但是整体看Git同步依旧不理想，一方面是在iPad中查看HTML文件一直很不方便（默认的HTML预览无法查看带有JavaScript代码的HTML文件，只有Microsoft Edge支持），所以这个方法虽然能在各个设备上通用，但还是不完美。

## WebDAV同步
这个同步方式是一个比较特殊的方式。WebDAV同步方式在2016年新增，只要将TiddlyWiki的HTML文件放在WebDAV文件夹中，然后用浏览器打开WebDAV链接，就能编辑TiddlyWiki文件。

但是，虽然许多网盘提供了WebDAV，但是并不是所有WebDAV都支持TiddlyWiki，比如：
* 没有网页端的WebDAV（如Nextcloud，坚果云），打开链接只会触发下载或查看纯文本
* 能打开文件但无法保存（如TeraCloud）

目前已知支持的有：

* 本地
  * rclone（以及安卓上的RCX）
  * wsgidav，Python上的WebDAV，可以在iOS的[a-Shell](https://holzschu.github.io/a-Shell_iOS/)上使用
  * [copyparty](https://github.com/9001/copyparty)，同样可以在a-Shell上使用
* 远程
  * Koofr（免费）
  * pCloud（付费）

本地的WebDAV可以用来在本地编辑TiddlyWiki。使用copyparty：

```sh
# 推荐用隔离的方式安装copyparty
# pipx install copyparty
uv tool install copyparty
mkdir tiddlywiki # 存放Tiddlywiki文件
cd tiddlywiki
```

默认情况下Copyparty在处理`PUT`请求时会存到另外一个文件，而不是覆盖原文件，因此要启用`daw`选项：

```sh
copyparty -v .::A:c,daw
```

启动后可以在[本地3923端口](http://127.0.0.1:3923)使用WebDAV保存。

也可以使用`wsgidav`（较麻烦，不推荐）：

```sh
pip install cheroot wsgidav
mkdir tiddlywiki # 存放Tiddlywiki文件
wsgidav --host 127.0.0.1 --port 80 --root tiddlywiki/ --auth anonymous
```

如果需要同步可以选择免费的Koofr网盘，在[Koofr](https://app.koofr.net)注册账号后生成令牌，然后将TiddlyWiki文件后缀名改为`.aspx`，上传至网盘。在浏览器访问以下链接：

```
https://app.koofr.net/dav/Koofr/文件.aspx
```
登录用户名为注册邮箱，密码为令牌，此时就可以打开TiddlyWiki了。

* * *
没错，这篇文章上次更新还是去年的6月16日，补写这个文章的原因是在2023年12月30日找到了iOS系统的本地WebDAV解决方案。目前这个文章终于可以完结了。

[Tiddlywiki官网]: https://tiddlywiki.com

[TiddlyHost]: https://tiddlyhost.com

[TiddlyDesktop]: https://github.com/TiddlyWiki/TiddlyDesktop

[Timimi]: https://ibnishak.github.io/Timimi/

[Tiddldroid]: https://f-droid.org/zh_Hant/packages/top.donmor.tiddloid/

[Quine]: https://apps.apple.com/cn/app/quine/id1450128957

[GitHub]: https://github.com

[GitLab]: https://gitlab.com

[Gitea]: https://gitea.com
