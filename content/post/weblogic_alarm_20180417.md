+++
draft = false
author = "q@shellpub.com"
title = "漏洞预警-WebLogic反序列化远程代码执行"
date = 2018-04-18T10:02:19+08:00
description = "CVE-2018-2628 Weblogic反序列化远程代码执行"
keywords = ["weblogic", "rce", "反序列化", "远程代码执行", "CVE-2018-2628"]
topics = ["weblogic", "漏洞预警"]
tags = ["weblogic","漏洞","预警"]
type = "post"
url = "/2018/04/18/weblogic_rce_alarm.html"
+++

<center>![](https://s1.ax1x.com/2018/04/18/CnaXrV.png)</center>


## 预警


 今日凌晨(北京时间2018-04-18)Oracle官方发布CPU（Critical Patch Update关键更新补丁)通告, 本次更新修复了一个未授权远程代码执行的反序列化漏洞CVE-2018-2628。河马安全研究员已就此漏洞进行了验证，已经成功复现此漏洞。本漏洞危害较大可被利用来挖矿，对用户造成严重损失，建议用户第一时间更新。

<center>![](https://s1.ax1x.com/2018/04/18/CnwgnP.png)</center>

## 关于WebLogic

WebLogic是美国Oracle公司出品的一个application server，确切的说是一个基于JAVAEE架构的中间件，WebLogic是用于开发、集成、部署和管理大型分布式Web应用、网络应用和数据库应用的Java应用服务器。将Java的动态功能和Java Enterprise标准的安全性引入大型网络应用的开发、集成、部署和管理之中。


## 影响范围

* Weblogic 10.3.6.0
* Weblogic 12.1.3.0
* Weblogic 12.2.1.2
* Weblogic 12.2.1.3

## 修复建议

	目前Oracle官方已经发布补丁，请移步
	http://www.oracle.com/technetwork/security-advisory/cpuapr2018-3678067.html
	安装对应的补丁
	
	如果在生产环境中，也可以临时禁用Weblogic T3协议，
	据称此种方法存在被绕过风险，建议及时验证兼容性，并安装最新官方补丁

	在安装补丁后建议使用河马WEBSHELL查杀客户端进行WEBSHELL检测和清理。

## 关于河马

	专注WEB安全研究与产品开发，有多年WEBSHELL清理检测经验

![](http://open.weixin.qq.com/qr/code?username=gh_d110440c4890)




## 参考
[oracle官方通告 http://www.oracle.com/technetwork/security-advisory/cpuapr2018-3678067.html](http://www.oracle.com/technetwork/security-advisory/cpuapr2018-3678067.html)  
[绿盟威胁情报 http://blog.nsfocus.net/category/threatalerts/](http://blog.nsfocus.net/category/threatalerts/)  
[白帽汇 漏洞预警](https://nosec.org/?token=xycxwt56je)