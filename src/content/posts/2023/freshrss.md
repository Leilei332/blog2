---
date: "\\<2023-01-08 Sun 11:23\\>"
description: FreshRSS
title: 重新使用RSS
---

```{=org}
#+filetags: 开源 RSS
```
RSS在很久以前就已经有了，作为一个历史悠久的技术，在这个信息爆炸的年代又有了新的意义。越来越多人开始重拾RSS。

我在之前用过很多本地RSS工具，不过后来都没怎么用。后来发现使用在线提供的RSS服务更加方便。目前仍然存活的RSS服务有：

- Feedly
- Inoreader
- The Old Reader
- FreshRSS

在这之中，Feedly已经在国内无法访问，Inoreader苟延残喘，只有一个镜像可以用[^1]，官方客户端是废的。其他一些服务没有被应用广泛支持。所以我选择了FreshRSS。

# 为什么选择FreshRSS

在目前用下来有很多RSS托管服务都是带有广告的，比如Inoreader和The Old Reader。而FreshRSS开源免费，没有任何广告。

FreshRSS这个服务原本是要自建的，不过[官网](https://freshrss.org)很良心，在下面可以找到 **Sign up to an existing server.** ，里面列出了现成的FreshRSS服务器列表，我选择了一个法国的服务器<https://rss.cheredeprince.net>。在那个列表里可以找到很多FreshRSS服务器，选一个注册即可。

# 应用端

在电脑上用FreshRSS直接用网页端就行了，而在移动端则最好使用应用来更好地阅读。

在安卓端推荐使用[FeedMe](https://github.com/seazon/FeedMe)，这个应用对各个平台的支持最广泛，也最漂亮。但是在较老的安卓版本可能会出现闪退的问题，解决方法是使用3.16的老版本。

当然在F-droid上也有很多其他支持FreshRSS的应用，有[Readrops](https://f-droid.org/packages/com.readrops.app)，但是对于同步阅读记录支持不佳。

在iOS上也有FreshRSS的客户端，推荐开源的NetNewsWire，这个应用也有Mac版本。

## 如何同步

订阅FreshRSS[^2]需要先生成一个API密码。在侧边栏点击"账户，找到"API管"，在上面密码框输入一个密码（注意这和账户密码不同）。

在Readrops里直接填上服务器地址，用户名，API密码就可以了。在FeedMe和NetNewsWire里还需要在服务器地址后面加上 `/api/greader.php` 。比如服务器是 `https://rss.cheredeprince.net/` ，填的地址就是 `https://rss.cheredeprince.net/api/greader.php` 。

# Footnotes

[^1]: 目前官方域名<https://inoreader.com>已经无法访问，只有另一个域名<https://innoreader.com>可以访问。

[^2]: 参考<https://cheredeprince.net/2018-09-09-Freshrss-sur-android/>
