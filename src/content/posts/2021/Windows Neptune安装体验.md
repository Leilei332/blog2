---
title: Windows Neptune安装体验
published: 2021-11-28
updated: 2021-12-12
slug: tw2022-windows-neptune
tags: 
- Tiddlywiki 2022归档
- 日志 2021
- Windows
- OS
---


在Windows 2000之后，Windows 内部出现了一个奇怪的分支：Windows Neptune和Windows Odyssey，其中Windows Odyssey很早就被放弃。这些计划在后面又被停止，最后又被运用在了Windows XP上。

关于这两个特殊版本的记录非常少，因为这些版本只留下了一个公开版本——Build 5111。

## 界面
最值得关注的就是Neptune的登录界面了，相较于Windows 2000单调的一个简陋的窗口和选择输入框，Neptune的用户可以有头像，默认的头像是一个海螺，似乎呼应了计算机语言中的shell。

仔细看的话，登录屏幕上的字看上去像IE渲染网页的字，这是因为这个登录屏幕是一个基于HTML和JS的HTA应用，在WinWorld上提示说安装IE6可能让登录屏幕停止运行。
TODO: [img[Screenshot_19991211_102543.png]]

说到用户，Neptune还有一个先进的“用户种类”特性，有四种用户，分别是Owner，Adult，Child，Guest，可以说是一个比较早的“家长控制”了。根据Winworld，Child类型用户可以控制使用时间已及屏蔽网页，而控制用户的*Windows Identities*还是HTA应用。

而别的方面就差不多了，基本跟Windows 2000一样，几乎一致的界面。而那个登录界面后来被改进，用到了Windows Whister上，也就是Windows XP的前身。而用户种类则被早早移除了。

## 参考
[WinWorld](https://winworldpc.com/product/windows-neptune/build-5111)

[BetaWiki](https://betawiki.net/wiki/Windows_Neptune_build_5111.1)



