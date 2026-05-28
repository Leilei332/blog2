---
title: Jupyter基本使用
published: 2021-04-28
updated: 2021-05-05
slug: j2021-jupyter
tags: 
- Joplin 2021补档
- 编程
- Python
---


![](https://gitee.com/xlbilly/lei-pic/raw/master/image.png "1")

现在越来越喜欢Web应用了，今天又开始搞起Jupyter了，操作和Mathematica比较像，虽然功能没Mathematica多，但是很轻量，代码也很容易学会。

一些使用体验上的问题:

## 更改默认ipynb文件存储位置
这个比较简单，首先在终端输入：

```sh
jupyter notebook --generate-config
```
然后在用户目录的.jupyter文件夹就会出现一个jupyter\_notebook\_config.py文件，找到c.NotebookApp.notebook\_dir = '' ，引号加入路径，去#号，linux端也一样。
这时linux段已生效，但windows端有问题，所以要改快捷方式才行。

## 开机自启动

在Linux里，新建/lib/systemd/system/jupyter.service文件，加入：

```ini
[Unit]
Description=jupyter notebook
After=network.target
[Service]
Type=simple
# 这里填用户名，下同
User=leilei
EnvironmentFile=/usr/bin/jupyter-notebook
ExecStart=/usr/bin/jupyter-notebook
ExecStop=/usr/bin/pkill /usr/bin/jupyter-notebook
KillMode=process
Restart=on-failure
RestartSec=30s
[Install]
WantedBy=multi-user.target
```
接下来是如何在Windows里开机自启Jupyter Notebook。


## cmd窗口问题

如果按普通启动，就会弹出一个窗口：
![](resources/92e78ca8b2ad402bbbc41f8ffc889a26.png)
~~这样也是不行的，所以我按照[这里](https://blog.csdn.net/qq_43479622/article/details/97495807)的方法，创建一个bat文件~~：
```powershell
%隐藏cmd窗口%
@echo off
if "%1"=="h" goto begin
start mshta vbscript:createobject("wscript.shell").run("""%~nx0"" h",0)(window.close)&&exit
:begin
cd /d D:\python\jupyter
jupyter notebook --no-browser
```
~~我在原来的基础上改了一些东西，那么之前创建的任务也要改了，这个bat文件双击就会有一个窗口一闪而过，不会分散注意力了。~~
以上方法过老，反正在我的Win10上没有成功，我在少数派上找到了一个[文章](https://sspai.com/post/66129)，可以通过Powershell隐藏窗口执行命令实现。

新建一个txt，后缀名改为ps1，写入以下内容：

```sh
cd D:/python/jupyter
jupyter notebook --no-browser
```

然后用“任务计划程序”创建一个基本任务，程序为`pwsh`（Windows自带的是`powershell`），参数为`-nop -w hidden -file C:/Users/admin/jupyter-notebook.ps1`（后面填ps1文件的路径），里面有一个巨坑：取消勾选“只有计算机使用交流电源时才启动此任务”，不然只有充电才能运行。完成试着运行一下。

**搞！定！**

## 设置密码

如果没设置密码，过一段时间Jupyter会要求输入Token（就是链接后面一大串的东西），为了避免麻烦，在下一次出现页面，在终端输入：

```sh
jupyter notebook list
```

在列出的东西找到?token=后面的东西，在下面的Token填入，在New Password输入新密码就行。

## 参考
[Linux下修改jupyter-notebook的默认路径](https://blog.csdn.net/yixi_370785/article/details/103721350)

[脚本启动和关闭 jupyter notebok 并隐藏命令行](https://blog.csdn.net/qq_43479622/article/details/97495807)

[Windows 本地自动化工具，任务计划程序应用举例](https://sspai.com/post/66129)