+++
draft = false
author = "q@shellpub.com"
date = 2018-07-18T14:12:10+08:00
title = "漏洞预警-WebLogic远程命令执行 CVE-2018-2893&CVE-2018-2894"
description = "CVE-2018-2893/CVE-2018-2894 Weblogic反序列化远程代码执行"
keywords = ["weblogic", "rce", "反序列化", "远程代码执行", "CVE-2018-2893"]
topics = ["weblogic", "漏洞预警"]
tags = ["weblogic","漏洞","预警"]
type = "post"
url = "/2018/07/18/weblogic_vul_alarm.html"
+++


<center>![](https://s1.ax1x.com/2018/04/18/CnaXrV.png)</center>


## 预警


 今日(北京时间2018-07-18)Oracle官方发布CPU（Critical Patch Update关键更新补丁)通告, 本次通告包含的一个反序列化漏洞CVE-2018-2893和远程命令执行CVE-2018-2894危害较大，可被利用来挖矿； 其中CVE-2018-2894漏洞可以直接通过HTTP方式利用，**[安全漏洞评分系统(CVSS)](https://blog.csdn.net/u012063507/article/details/72081820)高达9.8**，请站长朋友及时更新，或者使用一些防护产品，以免造成严重损失。

 	
<center>![](http://resource.shellpub.com/images/CVE20182894.png)</center>

## 关于WebLogic

WebLogic是美国Oracle公司出品的一个Application Server，确切的说是一个基于JAVAEE架构的中间件，WebLogic是用于开发、集成、部署和管理大型分布式Web应用、网络应用和数据库应用的Java应用服务器。将Java的动态功能和Java Enterprise标准的安全性引入大型网络应用的开发、集成、部署和管理之中。

Oracle 一般会在1，4，7，10月中距离17号最近的周二发布安全补丁包。本站上次WebLogic预警也是今年4月份的18号。

## 影响范围


* Weblogic 10.3.6.0
* Weblogic 12.1.3.0
* Weblogic 12.2.1.2
* Weblogic 12.2.1.3

## 修复建议

	目前Oracle官方更新建议请访问
	http://www.oracle.com/technetwork/security-advisory/cpujul2018-4258247.html

	建议使用河马查杀客户端检测WEBSHELL, 
<center>![](https://s1.ax1x.com/2018/07/18/P1t9fA.png)</center>
	
## 关于河马

	专注WEB安全研究与产品开发，有多年WEBSHELL清理检测经验

<center>![](http://open.weixin.qq.com/qr/code?username=gh_d110440c4890)</center>



## 参考
[oracle官方通告](http://www.oracle.com/technetwork/security-advisory/cpujul2018-4258247.html)  
[白帽汇 漏洞预警](https://nosec.org/home/detail/1705.html)  
[ADLab原创漏洞](https://mp.weixin.qq.com/s?__biz=MzAwNTI1NDI3MQ==&mid=2649613325&idx=1&sn=46ee799f72562d452c1ef668ce138f89&chksm=8306391db471b00bc43bc461d307aee239b75ad36a0bc387507e0b19da9a9364a27dd1fd3224&mpshare=1&scene=1&srcid=07188wbKZiEml7UL3KGnKFQw#rd)  
[漏洞预警-CVE-2018-2628 WebLogic反序列化远程代码执行](http://blog.shellpub.com/2018/04/18/weblogic_rce_alarm.html)  