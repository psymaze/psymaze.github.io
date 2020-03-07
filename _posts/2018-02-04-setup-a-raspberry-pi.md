---
layout: post
title: 树莓派入门小结

---

购入树莓派3B型一枚，还顺便买了官方出的萌萌的外壳，以及散热片。加上家里闲置的安卓充电插头和数据线，还有撸斐讯K2P时赠送的32GTF卡，正好可以让树莓派跑起来。作为树莓派新手，做一下我的入门小结。

**1. 烧录系统**
我选择的是官方推荐的[Raspbian OS](https://www.raspberrypi.org/downloads/raspbian/ "Raspbian OS")，是基于我比较熟悉的Debian 8 做的定制版，并带有图形桌面（注：这里使用BT下载速度更快）。使用[win32diskimager](https://sourceforge.net/projects/win32diskimager/ "win32diskimager")将下载得到的img烧录至TF卡中。烧录完毕后，在名为boot的TF卡的根目录中新建一个名为SSH的空文件。新建SSH.txt，再将后缀去掉即可。

**2. 开机**
将TF卡插入主板，连接上电源，再用网线连接路由器即可

**3. 连接SSH**
登录路由器的面板中可以清楚看到Raspberrypi分配到的IP地址。使用[putty](http://www.putty.org/ "putty")登录IP（端口为22），默认的用户名为pi，密码为raspberry。像Debian 8一样输入`passwd`更换默认密码。

**4. 更换源**
发现国内的网络连接到官方镜像实在太慢，更换成国内的源速度会比较快。我试了清华大学的源，我这里的网络连接依旧很慢，最后改成了阿里云的源了。

```
sudo nano /etc/apt/sources.list
```

在默认的源前面加如注释#，使其失效。在下方粘贴如下内容：

```
deb http://mirrors.aliyun.com/raspbian/raspbian/ jessie main non-free contrib rpi
deb-src http://mirrors.aliyun.com/raspbian/raspbian/ jessie main non-free contrib rpi
```

Ctrl+O回车保存，Ctrl+X退出nano编辑器

```
sudo nano /etc/apt/sources.list.d/raspi.list
```

在默认的源前面加如注释#，使其失效。在下方粘贴如下内容：

```
deb http://mirrors.aliyun.com/debian/ jessie main ui
```

Ctrl+O回车保存，Ctrl+X退出nano编辑器。最后执行`sudo apt-get update`即可。
不过我有点疑惑，是不是阿里云的镜像有些安装包没有呢？

**5. 开启WIFI**
插着网线太麻烦了，好在树莓派自带了WIFI模块。
这里我遇到了坑。使用wpa_supplicant.conf来启动WIFI失败。只好曲线救国，通过开启VNC来在图形桌面上开启WIFI。

```
sudo apt-get install tightvncserver
vncserver
```

注：分两次输入。根据提示创建8位数的VNC密码，之后就可以开启vncserver了。
电脑上打开[VNC Viewer](https://www.realvnc.com/en/connect/download/viewer/ "VNC Viewer")，在地址栏上输入`树莓派分配的IP:1`后就可以根据提示连接VNC并看到图形界面了。在树莓派可爱的界面的右上角，像使用PC一样连接WIFI吧。
连接上WIFI后可以断开网线使用WIFI连接了。不过这时注意树莓派分配到的IP地址会发生变更，需要重新查询。

以上就是我这个树莓派新手的入门总结。接下来就要好好想想要拿树莓派来做什么啦。

我购买VPS的时候有看到一些服务商有将树莓派托管在机房出租，想过去一排排可爱的树莓派乖乖地整齐地被放在机房里，有种萌感。CMour的小水管树莓派机房也已经搭建完成啦。

![树莓派](https://cdn.jsdelivr.net/gh/psymaze/psymaze.github.io//post-images/树莓派.jpg)