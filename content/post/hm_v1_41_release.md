+++
draft = false
author = "admin@shellpub.com"
date = 2018-06-04T14:05:02+08:00
description = ""
keywords = ["河马","后门", "发布", "webshell"]
title = "河马WEBSHELL扫描器1.4.1发布"
topics = ["后门"]
tags = [ "发版", "hm" ]
type = "post"
url = "/2018/06/04/hm_new_version141.html"
+++


# 河马查杀1.4.1 发布
<center>
![](http://blog.shellpub.com/images/2.png)
</center>

本次更新为修复性更新

## 下载地址

[windows版下载](http://down.shellpub.com/hm-ui/latest/HmSetup.zip?version=1.4.1)  
[linux64位下载](http://down.shellpub.com/hm/latest/hm-linux-amd64.tgz?version=1.4.1)  
[linux32位下载](http://down.shellpub.com/hm/latest/hm-linux-386.tgz?version=1.4.1)  


## 功能更新

  * 移除了一条存在误报的黑链检测规则

## BUG修正

  * windows 图形界面体验优化，在添加扫描目录时现在点击`添加扫描路径`的文字也能添加

## 已知问题

 * 最新版的kali下可能无法运行(内核4.14, 增加了一个GCC选项 https://github.com/golang/go/issues/20427), 如果您须要这个环境下的程序请通过本文下方的联系方式联系我们免费获取。
	

## 常见问题

1. 扫描失败，或者扫描文件数目为0

		软件限制了一些目录，例如Linux系统下/proc/目录文件不做检测，windows下C:/windows目录等

2. 扫描时崩溃

		请检查您使用的软件版本和操作系统版本是否匹配
		情检查您当前的用户是否为管理员用户

3. linux下没有找到可执行的文件

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

如果在使用过程中遇到问题，可以在本文下面留言或加<a href="tencent://message/?uin=1494922137&amp;Site=&amp;Menu=yes">QQ:1494922137</a>



	

