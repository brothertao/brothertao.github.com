---
layout: post
category : linux
tags : [linux, mount, umount, cifs]
---
{% include JB/setup %}

*** 问题 ***

	1. 首先mount一个Windows 共享
	2. 断开与Windows的链接
	3. umount挂载点，发现不能卸载

*** 解决 ***

	使用`umount -l`,注意是小写的L

[相关链接](http://stackoverflow.com/questions/40317/force-unmount-of-nfs-mounted-directory)

