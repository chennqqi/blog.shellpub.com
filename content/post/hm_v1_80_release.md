+++
draft = false
author = "admin@shellpub.com"
date = 2020-07-14T09:21:49+08:00
description = ""
keywords = ["河马", "后门", "发布", "webshell"]
title = "河马WEBSHELL扫描器1.8.0发布"
topics = ["后门"]
tags = [ "发版", "hm", "抽奖"]
type = "post"
url = "/2020/07/14/hm_new_version180.html"
+++


# 河马查杀1.8.0 发布[抽奖活动见文章末尾]
<center>
![](/images/2.png)
</center>

## 下载地址

[windows版下载](http://dl.shellpub.com/hm-ui/latest/HmSetup.zip?version=1.8.0)  
[linux64位下载](http://dl.shellpub.com/hm/latest/hm-linux-amd64.tgz?version=1.8.0)  
[linux32位下载](http://dl.shellpub.com/hm/latest/hm-linux-386.tgz?version=1.8.0)
  
[Linux版使用教程](http://www.shellpub.com/doc/hm_linux_usage.html)  
[windows版使用教程](http://blog.shellpub.com/2017/08/09/%E6%B2%B3%E9%A9%ACwebshell%E6%89%AB%E6%8F%8F%E5%99%A8v1_2.html)

## 功能更新

  本次更新集成**PHP深度解码器**，PHP深度解码在1.6.x时代完成初步开发，集成于在线查杀，经过几个版本的迭代，正式将PHP深度解码器下放到本地客户端，在使用深度解码器(deepscan)的情况下查杀速度较慢，建议先用常规模式(scan)进行快速查杀，再用深度查杀进行精准差查杀。
  另外：全新的查杀引擎2.0的研发工作已经启动，敬请关注！

* 集成**深度PHP解码器**，增强PHP类webshell检测能力
* linux系统支持扫描 `/srv` 目录, `/srv` 在之前的版本作为系统白名单目录被忽略
* 支持检测冰蝎v2.0.1后门
* 增加4条php文件检测规则，2条疑似文件检测规则
* 增加1条jsp疑似文件检测规则

## 如何使用深度模式

  深度解码模式命令格式为`hm deepscan <target dir>`

  下面动图演示了linux系统下先用scan模式进行扫描，接着使用deepscan进行扫描
  ![](/images/scan_vs_deepscan.gif)

	
  windows下可以在开始扫描按钮左侧勾选深度模式来决定是否启用深度解码器
  ![](/images/windows_deepscan.png)


## BUG修正

* 修复1.7.x版本遇到大文件后扫描缓慢的问题

## 已知问题

* 不支持内核2.6.18以下版本（即centos5系统默认内核版本)且无支持计划

## 兼容性测试


	|      OS    |      kernel     | version | arch | result |
	|------------|-----------------|---------|------|--------
	|  windows   |    -            | >=2003  | 32/64|   OK   |
	|  CentOS    |    >=2.6.32     | >=6     |      |   OK   |
	|  CentOS    |    <2.6.32      | < 6     | 32/64| 不支持  |
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

1. 已经联网，但是扫描程序依然报没有连接网络的错误

		可能的原因有两点： 一是您的操作系统时间与标准时间差距超过1分钟，使用ntp或者其他方式同步后问题解决； 
		二是您操作系统的PKI证书系统老旧，更新后即可解决，debian/ubuntu使用update-ca-certificates命令，centos使用
		update-ca-trust extract命令

2. 扫描失败，或者扫描文件数目为0

		软件限制了一些目录，例如Linux系统下/proc/目录文件不做检测，windows下C:/windows目录等

3. 扫描时崩溃

		请检查您使用的软件版本和操作系统版本是否匹配
		请检查您当前的用户是否为管理员用户

4. linux下没有找到可执行的文件

		请检查是否配置了环境变量或者使用./hm的方式来运行程序

5. 如何配置扩展名白名单

		在软件目录下有hm.yml文件，按照默认格式添加不需要被扫描的文件类型的扩展名
		jpg,png,gif不建议添加，有一类后门是隐藏在图片之中的。

6. 如何查看扫描结果

		扫描结果在扫描结束之后会保存到软件目录下的result.csv文件中，windows版可以在界面上直接查看结果

7. 如果安装了旧版软件是否能够自动更新

		linux环境下您可以在软件所在目录执行`hm update`命令，软件会自动升级到最新版本
		windows版检测到可更新版本后点击下载新版本

8. 如何让软件不输出中文，只输出英文

		linux配置环境变量HM_LANG=zh-CN则强制显示中文；配置HM_LANG=en-US强制显示英文系统

9. 我不想下载软件如何快速检测

		可以使用在线查杀https://n.shellpub.com,上传源代码zip包即可，需要注意的是上传大小限制为20MB

10. 检测结果不准确？

		可以通过文章下方的联系方式联系我们，我们有专业的安全工程师跟您对接
	
## 

如果在使用过程中遇到问题，可以在本文下面留言或加<a href="tencent://message/?uin=1494922137&amp;Site=&amp;Menu=yes">QQ:1494922137</a>


## 关注我们参与抽奖

![](http://open.weixin.qq.com/qr/code?username=gh_d110440c4890)
****

活动时间： 2020-07-15-2020-07-29

活动一：
关注公众号，转发文章https://mp.weixin.qq.com/s/PXpOpV5meuqWLLso35pxMg
截图在公众号后台回复，我们会抽出两位幸运读者，送出《互联网安全建设从0-1》

活动二：
使用河马查杀，在公众号后台提建议，最优两条建议送出《互联网安全建设从0-1》
