---
title: 数字难民——Windows 8.1在2024年的现状
published: 2024-01-08
updated: 2024-01-13
tags: 
- Windows
slug: windows-8-in-2024
---


最近又给老笔记本重装了Windows 8.1系统（没错，是在写[](#%E8%80%81%E7%AC%94%E8%AE%B0%E6%9C%AC%E4%B8%8ALinux%E4%BD%BF%E7%94%A8%E4%BD%93%E9%AA%8C)这个文章的5个月后[^1]，目前这个文章还没有完结），在去年的1月10日，Windows 8.1停止支持，在一年后使用这个操作系统不出意外遇到了许多阻力。

列举一下Windows 8.1目前不支持的框架：

* Qt 6，目前Qt6框架仅支持Windows 10以上版本
* .NET Framework 4.8.1，Windows 8.1支持的版本为4.8
* Electron 23，在Windows 8.1中运行会报错

目前以下软件最新版本仍然支持Windows 8.1

* Git
* msys2
* Rainmeter
* Firefox

目前以下软件放弃了对Windows 8.1的支持：

* Anki，连Qt5版本也不支持，最后一个支持的版本为2.1.49
* Visual Studio Code，最新版运行报错
* Joplin，运行报错，最后一个支持的版本为2.12.3
* Chrome，最后一个支持的版本为109.0
* qBittorent，目前能用的版本为4.2.0
* iTunes，目前能用的版本为12.10
* OBS Studio，由于在新版中用了Qt6而不支持，这个应该算第一批放弃支持Windows 8.1的（2023年夏）

* * *
不过比这个问题还重要的是一个硬件问题—目前笔记本的屏幕从显示彩线已经变成现在频繁出现暗屏的问题，可能需要去报修。

[^1]: 事实说明即使尽可能多地关掉了KWin的桌面特效，Linux运行的流畅程度还是与电脑本身的硬件有关。另外虽然有Xfce甚至是Tiling Window Manager可供选择，这些桌面环境也对触屏支持不友好。