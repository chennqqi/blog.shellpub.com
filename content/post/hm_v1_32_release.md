+++
draft = false
author = "admin@shellpub.com"
date = "2017-12-22T09:31:21+08:00"
description = ""
keywords = ["河马","后门", "发布", "webshell"]
title = "河马WEBSHELL扫描器1.3.2发布"
topics = ["后门"]
tags = [ "发版", "hm" ]
type = "post"
url = "/2017/12/22/hm_new_version132.html"
+++

# 河马查杀1.3.2 发布
<center>
![](/images/2.png)
</center>

近期不少用户反馈扫描时异常崩溃，我们调试后发现在获取版本失败导致的此问题，这个版本主要是修复这个BUG。
今日冬至，大家大吉大利，晚上吃鸡和饺子！


## 下载地址

[windows版下载](http://down.shellpub.com/hm-ui/latest/HmSetup.zip?version=1.5.0)  
[linux64位下载](http://down.shellpub.com/hm/latest/hm-linux-amd64.tgz?version=1.5.0)  
[linux32位下载](http://down.shellpub.com/hm/latest/hm-linux-386.tgz?version=1.5.0)  


## 功能更新

* 增加反馈页面

## BUG修正

* 修正版本号获取失败时界面崩溃的BUG

## 优化

* 之前版本CGO DNS请求需要配置环境变量，这个版本直接集成到软件之中了
* UI首页增加官方QQ，方便客户即时沟通


## 常见问题

1. 扫描失败，或者扫描文件数目为0

		软件限制了一些目录，例如Linux系统下/proc/目录文件不做检测，windows下C:/windows目录等

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

如果在使用过程中遇到问题，可以在本文下面留言或加<a href="tencent://message/?uin=1494922137&amp;Site=&amp;Menu=yes">QQ:1494922137</a>



	



		