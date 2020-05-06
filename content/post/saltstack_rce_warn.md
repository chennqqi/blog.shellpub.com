+++
draft = false
author = "admin@shellpub.com"
title = "saltstack RCE安全通告"
keywords = ["CVE-2020-11651", "CVE-2020-11652", "saltstack", "RCE", "漏洞预警" ]
date = 2020-05-06T11:42:31+08:00
description = "saltstack漏洞挖矿排查"
topics = ["漏洞预警"]
tags = ["vulnerable","漏洞","预警","运维"]
type = "post"
url = "/2020/05/06/saltstack多版本RCE安全通告.html"
+++


<center>![](/images/salt/saltstack.jpeg)</center>


## 安全通告

Saltstack 定位是自动化运维工具，运维工具一旦出现漏洞危害影响较大。同类型的运维工具还有[ansible](https://www.ansible.com),[puppet](https://puppet.com/),[Chef](https://www.chef.io/)

国外安全团体F-Secure报告了两个Saltstack漏洞

包含两个CVE

- CVE-2020-11651 水平权限绕过漏洞
- CVE-2020-11652 任意文件读写漏洞

通过对这两个漏洞的利用可以实现RCE的效果，在控制salt-master之后，通过salt大面积控制在运维系统下的主机

## 关于saltstack

SaltStack是基于Python开发的一套C/S架构配置管理工具，是一个服务器基础架构集中化管理平台，具备配置管理、远程执行、监控等功能，基于Python语言实现，结合轻量级消息队列（ZeroMQ）与Python第三方模块（Pyzmq、PyCrypto、Pyjinjia2、python-msgpack和PyYAML等）构建。


## 影响范围

SaltStack < 2019.2.4
SaltStack < 3000.2


## 问题排查

**1.查看进程**`ps -ef|grep salt`
![](/images/salt/process.png)
如图所示为阿里云中某机器中招后截图，其中三个salt相关进程。
`alicloud-salt-minion` 为官方进程
`/tmp/salt-minions` 为挖矿样本

md5sum /tmp/salt-minions 计算挖矿样本hash为

目前已知恶意hash如下：
- a28ded80d7ab5c69d6ccde4602eef861
- 8ec3385e20d6d9a88bc95831783beaeb
- 2c5cbc18d1796fd64f377c43175e79a3
- dc5b2fa7f85aa0bbd226afe3b5fcaeea
- defc9efd1b430aea797e573922fa49ae

file命令查看文件类型，挖矿进程为elf文件
![](/images/salt/file.png)

正常文件为python脚本文件
![](/images/salt/file2.png)

**2.检查网路链接**`netstat -anp|grep tcp|grep ESTABLISHED`
![](/images/salt/connection.png)
如图所示，排除掉本地连接、排除掉入向链接，观察外连进程状态。

已知挖矿主机远程IP如下：
- 217.12.210.192
- 206.189.92.32

**3.阿里云安全面板通知**
![](/images/salt/aliyun.png)
如果您使用的阿里云，可以在安全面板上看到如图类似告警，请注意关注安全告警

**4.其他行为**
目前发现该挖矿程序会关闭cpu占用较高的进程，在系统日志里可以查看到kill记录`grep -r "kill" /var/log/messages*`

![](/images/salt/message.png)
也会关闭docker中的其他挖矿程序


## 修复建议

1. 建议重装系统，因为salt进程权限为root权限，理论上被黑后，黑客拥有任意权限，可能种入隐藏后门。如果暂时无法重装系统可以使用阿里云提供的一键清理脚本`curl https://ageis-check.oss-cn-hangzhou.aliyuncs.com/salt_miner_clean.sh | /bin/bash`
2. 升级到安全版本
2019.2.4
3000.2
3. 打开saltstack自动更新
4. Salt Master所在机器的防火墙、安全组上配置策略，只允许可信ip访问4505和4506端口


## 关于河马

	专注WEB安全研究与产品开发，有多年WEBSHELL清理检测经验

![](http://open.weixin.qq.com/qr/code?username=gh_d110440c4890)


## 参考
[阿里云漏洞预警https://help.aliyun.com/noticelist/articleid/1060284512.html](https://help.aliyun.com/noticelist/articleid/1060284512.html)  

[360Cert漏洞通告](https://cert.360.cn/warning/detail?id=f31be92efc1ab6e8a09b987411a9759a)

[SaltStack漏洞导致的挖矿排查思路 https://www.cnblogs.com/lxmwb/p/12831030.html](https://www.cnblogs.com/lxmwb/p/12831030.html)

[CVE-2020-11651 AKA SaltStack RCE](https://gist.github.com/SwitHak/8e7fa45b5656c691ddf13c8c47e8fda6)

[SaltStack authorization bypass](https://labs.f-secure.com/advisories/saltstack-authorization-bypass)

[https://github.com/vulhub/vulhub/tree/master/saltstack](https://github.com/vulhub/vulhub/tree/master/saltstack)

[针对SaltStack远程命令执行漏洞（CVE-2020-11651、CVE-2020-11652）植入挖矿木马的应急响应 https://s.tencent.com/research/report/975.html](https://s.tencent.com/research/report/975.html)

[https://github.com/vulhub/vulhub/tree/master/saltstack](https://github.com/vulhub/vulhub/tree/master/saltstack)