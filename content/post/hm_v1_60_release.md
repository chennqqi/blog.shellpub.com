+++
draft = true
author = "admin@shellpub.com"
date = 2019-09-25T10:08:32+08:00
description = ""
keywords = ["河马","后门", "发布", "webshell"]
title = "河马WEBSHELL扫描器1.6.0发布"
topics = ["后门"]
tags = [ "发版", "hm" ]
type = "post"
url = "/2019/09/25/hm_new_version150.html"
+++


# 河马查杀1.6.0 发布
<center>
![](http://blog.shellpub.com/images/2.png)
</center>

本次更新为修复性更新

## 下载地址

[windows版下载](http://dl.shellpub.com/hm-ui/latest/HmSetup.zip?version=1.6.0)  
[linux64位下载](http://dl.shellpub.com/hm/latest/hm-linux-amd64.tgz?version=1.6.0)  
[linux32位下载](http://dl.shellpub.com/hm/latest/hm-linux-386.tgz?version=1.6.0)
  
[Linux版使用教程](http://www.shellpub.com/doc/hm_linux_usage.html)  
[windows版使用教程](http://blog.shellpub.com/2017/08/09/%E6%B2%B3%E9%A9%ACwebshell%E6%89%AB%E6%8F%8F%E5%99%A8v1_2.html)



## 功能更新

  * 新增hmdocker --docker版的查杀，以适配更多的linux发行版
  * 重写了asp解码，取消跨语言调用；这个特性会导致扫描asp文件速度变慢，但可以检出更多的asp文件webshell
  * 增加jar文件检测，检测方法同war文件； 如果您不需要检测jar文件，可以在hm.yml中忽略jar文件
  * 适配Kali系统
  * 新增规则
  * 支持检测phpstudy DLL后门

## BUG修正

  * 修复扫描文件时指定输出路径(-output参数)无效的BUG

## 已知问题

 * 不支持内核2.6.18以下版本（即centos5系统默认内核版本)且无支持计划

## 兼容性测试


	|      OS    |      kernel     | version | arch | result |
	|------------|-----------------|---------|------|--------
	|  windows   |    -            | >=2003  | 32/64|   OK   |
	|  CentOS    |    >=2.6.18     | >=5     |      |   OK   |
	|  CentOS    |    <2.6.18      | < 5     | 32/64| 不支持  |
	|  Ubuntu    |    -            |  -      |      |   OK   |
	|  Kali      |    -            | 2.0,2019| 32/64|   OK   |
	|  Kali      |    -            | <2.0    | 32/64|   -    |
	|  SuSE      |    -            | -       |      |   -    |
	|  Debian    |    -            | -       |      |   -    |
	|  Fedora    |    -            | -       |      |   -    |
	|  Redhat    |    -            | -       |      |   -    |


- **OK** 表示测试通过, 可以正常运行
- **不支持** 表示官方没有计划支持此版本
- **-** 表示未经测试，但是理论上支持

如果您在使用中发现不兼容的发行版本请和我们联系，文章末尾有我们的联系方式


## 常见问题

1. 已经联网，但是扫描程序依然报没有连接网络

		可能的原因有两点： 一是您的操作系统时间于标准时间差距超过1分钟，使用ntp或者其他方式同步后问题解决； 
		二是您操作系统的PKI证书系统老旧，更新后即可解决，debian/ubuntu使用update-ca-certificates命令，centos使用
		update-ca-trust extract命令


2. 扫描失败，或者扫描文件数目为0

		软件限制了一些目录，例如Linux系统下/proc/目录文件不做检测，windows下C:/windows目录等

3. 扫描时崩溃

		请检查您使用的软件版本和操作系统版本是否匹配
		情检查您当前的用户是否为管理员用户

4. linux下没有找到可执行的文件

		请检查是否配置了环境变量或者使用./hm的方式来运行程序

5. 如何配置扩展名白名单

		在软件目录下有hm.yml文件，按照默认格式添加不需要被扫描的文件类型的扩展名
		jpg,png,gif不建议添加，有一类后门是隐藏在图片之中的。

6. 如何查看扫描结果

		扫描结果在扫描结束之后会保存到软件目录下的result.csv文件中，windows版可以在界面上直接查看结果

6. 如何实现定时扫描

		linux利用系统crontab，在crontab中添加定时扫描任务。

8. 如果安装了旧版软件是否能够自动更新

		linux环境下您可以在软件所在目录执行`hm update`命令，软件会自动升级到最新版本
		windows版检测到可更新版本后点击下载新版本
	
## 

如果在使用过程中遇到问题，可以在本文下面留言或加<a href="tencent://message/?uin=1494922137&amp;Site=&amp;Menu=yes">QQ:1494922137</a>

