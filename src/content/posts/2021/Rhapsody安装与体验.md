---
title: Rhapsody安装与体验
published: 2021-04-09
updated: 2021-04-30
slug: j2021-rhapsody
tags: 
- Joplin 2021补档
- OS
- Apple
---


在苹果公司把NeXT.Inc收购后，就决定把NeXTSTEP的内核Mach作为Mac OS X的内核，Rhapsody就是在OPENSTEP 4.x的基础上魔改而来的一个测试版本，而在之后的正式版本则用了Darwin内核，当然这个后面细讲。

虽然Rhapsody提供PowerPC版本，但是我亲身实验过在MacOS 9.2里是不能安装的！同意协议后就直接卡死……

![](https://gitee.com/xlbilly/lei-pic/raw/master/image-20210403222517163.png)

![看看就好](https://gitee.com/xlbilly/lei-pic/raw/master/qemu-system-ppc_oH1bWJMZc8.png "看看就好")

## Grazil x86 DR1

![](https://gitee.com/xlbilly/lei-pic/raw/master/86Box_JNqPhUpZ87.png)

这是Rhapsody的第一个测试版本，可以看到很多地方都是“照搬”了NeXTSTEP，比如说底部的Dock，根目录的NeXTAdmin文件夹等。顶部的标签有MacOS 9那味了。

相比NeXTSTEP，Rhapsody增加了桌面，这是NeXTSTEP没有的，不过这个版本的文件窗口和NeXTSTEP一样居然是不能关的，很鸡肋。

说道这个文件管理器，可以看到文件夹的图标有MacOS 9那味了，窗口下面还增加了个人文件夹，往上，新建文件夹等快捷操作按钮。在左上角的苹果图标里的"About Workplace Manager"里的关于页面跟NeXTSTEP完全一致，下面还可以看到"Developed with OPENSTEP"字样。

![](https://gitee.com/xlbilly/lei-pic/raw/master/20210405223658.png)

当然，里面还包含一些NeXTSTEP的身影，如果打开Configure.app，就会出现经典的窗口和右上角的任务栏。里面还复刻了MacOS 9.2的Stickies.app。

![](https://gitee.com/xlbilly/lei-pic/raw/master/86Box_MyZKerbBAr.png)

## Titan x86 DR2

Titan版本在之前的Grazil版本有了很大改进，底部Dock栏被移除，取而代之的是右上角的经典应用切换器，文件管理器的窗口也可以关闭了，增加了列表查看方式。

![](https://gitee.com/xlbilly/lei-pic/raw/master/86Box_xxbVyzv3HZ.png)

而图标也进行了重新设计，和MacOS很像，根目录也取消了NeXTSTEP的命名方式。比如NextAdmin变成了Administration，NextDeveloper也一样

![](https://gitee.com/xlbilly/lei-pic/raw/master/86Box_Qydzo8qw1a.png)

还有一个变化是：第一次进入时会进入Setup Assistant，而不是NeXTSTEP的欢迎页面。

![录屏时截的](https://gitee.com/xlbilly/lei-pic/raw/master/20210405222313.png)

当然，这次更新也带回了一些NeXTSTEP的东西，比如说登录屏幕：

![原版登录错误窗口摇头效果](https://gitee.com/xlbilly/lei-pic/raw/master/nextsteplogin.gif)

![](https://gitee.com/xlbilly/lei-pic/raw/master/rhapsodylogin.gif)