---
layout: post
title: "经典实用的Shell命令"
date: 2012-12-24 09:02
comments: true
categories: shell 
---
**1、ls -AQ|grep -v proc|xargs du -sh|sort -h**

按从小到大的顺序显示根目录下除proc目录以外的所有文件及目录大小（须在根目录下执行该命令）

**2、dpkg -l |grep ^rc |awk '{print $2}' |xargs dpkg --purge**

删除已删除包的残留配置文件（Debian分支）

**3、find . -type f -print |xargs du -sb |sort -h**

查找当下目录及其子目录下面的所有文件，并按文件大小，由小到大排序
