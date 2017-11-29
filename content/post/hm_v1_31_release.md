+++
draft = false
author = "admin@shellpub.com"
date = "2017-11-29T09:31:21+08:00"
description = ""
keywords = ["河马","后门", "发布"]
title = "河马扫描器1.3.1发布"
topics = ["后门"]
tags = [ "发版", "hm" ]
type = "post"
url = "/2017/11/29/hm_new_version.html"
+++

# 
<center>
![](http://blog.shellpub.com/images/2.png)
</center>

* 下载

[windows版下载](http://down.shellpub.com/hm/1.3.1/hm-windows-386.zip)  
[linux64位下载](http://down.shellpub.com/hm/1.3.1/hm-linux-amd64.tgz)  
[linux32位下载](http://down.shellpub.com/hm/1.3.1/hm-linux-386.tgz)  


## 功能更新

* 增加一条绕过规则
* 增加了门罗币挖矿脚本检测
* 支持离线模式下深度查杀

## BUG修正

* 修正某些特殊文件路径无法检测的BUG
* 修正了一个中英文翻译显示不正确的BUG

## 优化

* 优化了文件包含类后门检测
* 优化白名单，允许扫描linux /mnt目录，windows桌面目录

## 已知问题

* 在部分linux系统(ubuntu等)DNS由于cgo自身问题(参考链接<https://yq.aliyun.com/articles/238940>)导致发请求时崩溃, 解决办法
		
	
		在环境变量中加入
		
		export GODEBUG=netdns=go

## 常见问题

1. 扫描失败，或者扫描文件书目为0

		软件限制了一些目录，例如Linux系统下/proc/目录文件不做检测，linux下C:/windows目录等

2. 扫描时崩溃

		请检查您使用的软件版本和操作系统版本是否匹配
		最常见导致崩溃的就是系统cgo兼容新问题，解决办法参考#已知问题

3. 没有找到可执行的文件

		请检查是否配置了环境变量或者使用./hm的方式来运行程序

4. 如何配置扩展名白名单

		在软件目录下有hm.yml文件，按照默认格式添加不需要被扫描的文件类型的扩展名
		jpg,png,gif不建议添加，有一类后门是隐藏在图片之中的。

5. 如何查看扫描结果

		扫描结果在扫描结束之后会保存到软件目录下的result.csv文件中，windows版可以在界面上直接查看结果

6. 如何实现定时扫描

		linux利用系统crontab，在crontab中添加定时扫描任务。

7. 如果安装了旧版软件是否能够自动更新

		linux环境下您可以在软件所在目录执行`hm update`命令，软件会自动升级到最新版本
	
## 

如果在使用过程中遇到问题，可以在本文下面留言或添加<a href="tencent://message/?uin=1494922137&amp;Site=&amp;Menu=yes">QQ:1494922137</a>



	



		