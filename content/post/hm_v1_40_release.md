+++
draft = false
author = "admin@shellpub.com"
date = "2018-01-29T21:31:21+08:00"
description = ""
keywords = ["河马","后门", "发布", "webshell"]
title = "河马WEBSHELL扫描器1.4.0发布"
topics = ["后门"]
tags = [ "发版", "hm" ]
type = "post"
url = "/2018/01/29/hm_new_version140.html"
+++

# 河马查杀1.4.0 发布
<center>
![](/images/2.png)
</center>

随着weblogic漏洞（CVE-2017-3506)的爆发，近期挖矿程序猖獗; 本次更新主要增加了几个挖矿程序的检测规则。

增加:

  * 黑链、暗链的检测规则
  * 恶意挖矿脚本检测规则
  * 恶意挖矿程序检测规则


## 下载地址

[windows版下载](http://down.shellpub.com/hm-ui/latest/HmSetup.zip?version=1.5.0)  
[linux64位下载](http://down.shellpub.com/hm/latest/hm-linux-amd64.tgz?version=1.5.0)  
[linux32位下载](http://down.shellpub.com/hm/latest/hm-linux-386.tgz?version=1.5.0)  


## 功能更新

* 升级查杀引擎，提高查杀速度

## BUG修正

* 修正版界面上扫描时间总是被累计，不会重置的BUG

## 已知问题

	windows环境下，由于权限问题，有小概率导致扫描崩溃（测试环境无法复现），如果您遇到这个问题，请联系我们。

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



	



		