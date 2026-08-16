---
title: 安卓上的Python
published: 2022-01-12
updated: 2022-01-23
slug: tw2022-python-on-android
tags:
- Tiddlywiki 2022归档
- Android
- 软件
- Python
---


最近在网上找如何在Android上使用Python的办法，最后找到了一个目前看下来很满意的App——QPython

## 为什么选择QPython
网上在手机上运行Python的方法有很多，有Pydroid，Termux。以下是选择QPython的原因：

* **开源免费**。Pydroid是需要收费的。
* **兼容性强**。QPython OS对手机要求很低，很老的Android系统也支持运行，QPython 3S甚至支持到2.3的版本。而Termux和Pydroid的最新版本早已抛弃Android 5.0和arm32平台。
* **功能多**。Termux只能做终端交互，而QPython可以用androidhelper做GUI，甚至运行Jupyter Notebook！

## androidhelper库
androidhelper是QPython内置的库，可以提示信息，弹出弹窗等。QPython内置了一个hello_world.py，代码如下：

```python
import androidhelper
droid=androidhelper.Android()
droid.makeToast("Hello World!")
print("Hello World")
```

在参考了androidhelper的API后，我自己做了一个简单的脚本：

```python
import androidhelper
droid=androidhelper.Android()
va=droid.dialogGetInput(title='名字',message='输入：')
droid.notify('你好！','你好，'+va.result+'！')
```
这个示例会弹出一个窗口让人输入名字，然后会弹出一个标题为`你好`，内容为`你好，【名字】！`。

## 其他
Python自带pip安装模块，QPython也有pip，以及自带的源QPypi。不过这个源自带的模块也就那么几个，有matplotlib，numpy，pandas，scipy这些常用的模块。我试了装一下matplotlib却报了错。当然用常规的Python源也行，我试着装了一下pyecharts，但自带Python太老了。

如果在控制台按钮上长按，还有更多选项，有Jupyter笔记本，普通shell。Jupyter笔记本要手动开QPyNotebook，最后终于可以在应用内使用了，唯一的问题是不能用matplotlib。

QPython虽然能编辑文件，但还是非常麻烦，所以里面还提供了扫码功能，只要生成一个二维码再扫码就可以了。

```python
pip install qrcode
```

