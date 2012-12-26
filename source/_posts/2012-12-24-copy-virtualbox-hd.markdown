---
layout: post
title: "VirtualBox中复制使用虚拟硬盘"
date: 2012-12-24 22:56
comments: true
categories: [VirtualBox, linux, vm, it] 
---
VirtualBox可不像VMware那样，直接复制虚拟磁盘文件就可以了事的，只因为VirtualBox识别虚拟磁盘文件VDI采用了uuid识别技术。

由于测试需要搭建局域网环境，需要两台虚拟机同时运行。当我安装完一个虚拟系统时，我将虚拟磁盘文件复制一份重新创建虚拟系统时提示打开虚拟硬盘 windowsxp.vdi 失败。
    
    Cannot register the hard disk 'windowsxp.vdi' with UUID {24eb969f-8c98-470d-b2dd-35318f2b8860} 
    because a hard disk 'windowsxp.vdi' with UUID {24eb969f-8c98-470d-b2dd-35318f2b8860} already exists 
    in the media registry ('/home/sager/VirtualBox VMs/windowsxp/windowsxp.vid').

往Google里找寻了一番，原来Virtualbox也是有VBoxManage命令的,于是我决定给复制的vdi文件重新分配uuid。
<!-- more -->
```bash 重新分配uuid
sager@sager-desktop:~/VirtualBox VMs/WinXP>VBoxManage internalcommands sethduuid windowsxp.vdi 
UUID changed to: c8acda7d-149d-4157-affb-2d2dbc1bab7
```
接着就可以使用拷贝的vdi文件正常的创建第二台虚拟机了。

当然如果你没有直接复制vdi文件,那么直接用Virtualbox自带的克隆vdi文件命令。
```bash 自带克隆vdi文件
sager@sager-desktop:~/VirtualBox VMs/WinXP>VBoxManage clonehd windowsxp.vdi winxp.clone.vdi
```

Virualbox的快照功能非常不错,可以即时恢复到快照时的状态，做试验就不用重新配环境了。
