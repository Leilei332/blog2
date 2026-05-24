---
title: Mac OS X 早期版本安装
published: 2021-04-20
updated: 2021-04-30
tags: 
- 补档
- OS
- Apple
---


![](https://gitee.com/xlbilly/lei-pic/raw/master/qemu-system-ppc_YpxgNrqtzL.jpg)



## 安装

首先确保Qemu已安装，配置好环境变量，准备好Mac OS 10.0的安装镜像，用`qemu-img`新建好磁盘，然后终端输入：

```sh
qemu-system-ppc.exe -L pc-bios -boot d -m 512 -M g3beige -prom-env "auto-boot?=true" -prom-env "boot-args=" -prom-env "vga-ndrv?=true" -drive file="path/to/iso/file.iso",format=raw,media=cdrom -drive file=hdimage.img,format=raw,media=disk -sdl -netdev user,id=network01 -device sungem,netdev=network01 -usb -device usb-kbd -device usb-mouse
#path/to/iso/file.iso填Mac OS 10.0安装镜像的路径
#hdimage.img填新建的磁盘的位置
```

在标签栏的"Installer"选择"Open disk utility"，在"Drive Setup"里找到/dev/disk0，选择，点击里面的"Partition"标签栏，上面选择"1 Partition"，点击"Partition"，完成后在标签栏选择退出。

然后就是一步一步来了，在选择安装位置时一定要勾上下面的框，将磁盘重新格式化，然后安装完就好了。

![](https://gitee.com/xlbilly/lei-pic/raw/master/20210421184038.png)

> 注意：必须先在磁盘工具里格式化好磁盘，否则在选择安装位置时会不显示硬盘，**而不勾下面的框将导致系统无法启动！**

安装完成，把之前的命令里的`-boot d`改成`-boot c`，运行，应该可以看到这个界面：

![](https://gitee.com/xlbilly/lei-pic/raw/master/20210422101213.png)

这里就是下一步下一步，不过在填个人信息界面会看到这个：

![](https://gitee.com/xlbilly/lei-pic/raw/master/20210422103103.png)

这是最坑的一步，"Zip Code"要填五位数字，右边的"Area Code"可以填三位数字如456，"Phone Number"要填成XXX-XXXX，而且前三位也有要求，所以避免踩坑可以填华盛顿的456，例如：456-1234

然后应该没有问题，**不过不要连接网络！**,为了避免踩坑，请进行以下操作：

> 在**Get Internet Ready**里，选择I'm not ready to connect the Internet，然后选Yes。

> 在**Get iTools**里，选择I'm not ready for iTools。

> 在**Connecting**里，选择Cancel。

这样，你就完美地绕过了所有的坑。不出意外应该能看到这个界面：

![](https://i.loli.net/2021/04/22/Vd251F4ZgWzLykJ.png)

## 体验

![](https://gitee.com/xlbilly/lei-pic/raw/master/qemu-system-ppc_YpxgNrqtzL.jpg)

首先开机会出现一个这样的界面，中间有一个麦金塔电脑的图标，有点像Mac OS 9的一闪而过的画面

![](https://gitee.com/xlbilly/lei-pic/raw/master/Screenshot_20210430_152940.png)

早期版本的Mac OS其实还是保留着NeXTSTEP的影子，这个鼠标光标就是从NeXTSTEP的光标搬运过来的，直到10.2版本才进行了重新设计，但还是和NeXTSTEP像。

Qemu模拟的动画效果比我想象中还丝滑，Aqua UI设计也有耳目一新的感觉，至少比当时的Windows 2000好多了，除了最小化外，这个动画我也玩了很久：

![](https://gitee.com/xlbilly/lei-pic/raw/master/osx.gif)

这个动画效果说实话一点用都没有，但是看着挺酷炫，就像小米自带的地球动态壁纸和苹果应用图标彩蛋一样，也只能说明苹果在UI细节上确实很用心。

除此之外，UI的细节做得很好，对话框闪烁的按钮，水滴似的按钮，高清的拟物化图标算是当时细节很丰富的了。

而注销之后就可以看到登录屏幕了，跟Rhapsody的登录屏幕很像，只是之前的正方形按钮换成了圆形水滴按钮，LOGO的文字阴影效果也很好：

![](https://gitee.com/xlbilly/lei-pic/raw/master/Screenshot_20210421_123744.png)

## 参考
[Winworld:Mac OS X 10.0](https://winworldpc.com/product/mac-os-x/100)

[还看今朝 —— Qemu，更完善的Power Mac模拟 （二）（使用心得篇）](https://zhuanlan.zhihu.com/p/107262874)

[Mac 视觉史（三）：浴「水」重生的 Mac 视觉美学](https://sspai.com/post/60888)