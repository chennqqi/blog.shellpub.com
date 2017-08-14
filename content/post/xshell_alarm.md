+++
draft = false
author = "admin@shellpub.com"
date = "2017-08-14T15:31:21+08:00"
description = "XSHELL存在后门"
keywords = ["xshell","后门", "SSH"]
title = "XSHELL多版本存在后门"
topics = ["后门"]
tags = [ "linux", "后门","SSH"]
type = "post"
url = "/2017/08/14/XSHELL_WITH_BACKDOOR.html"
+++


# 安全通告--终端软件XSHELL多版本存在后门

据[360安全客](http://bobao.360.cn/news/detail/4263.html)与360CERT消息，知名linux终端软件XSHELL存在后门，而且是官方版本。包括XSHELL软件单体和其安装套件Xmanager.

![](http://p8.qhimg.com/t012374abe2cafc2529.png)

XSHELL是一个强大的安全终端模拟软件，它支持SSH1, SSH2, 以及Microsoft Windows 平台的TELNET 协议。详细介绍请看[这里](https://baike.baidu.com/item/Xshell/5659054)


## 存在后门的版本

- Xshell Build 5.0.1322

- Xshell Build 5.0.1325

- Xmanager Enterprise 5.0 Build 1232

- Xmanager 5.0 Build 1045

- Xftp 5.0 Build 1218

- Xftp 5.0 Build 1221

- Xlpd 5.0 Build 1220

## 修复建议

建议用户使用以下步骤进行修复

1. **升级XSHELL及其套件到最新版本**
2. **修改linux服务器系统密码；在可能的情况下使用key+passphrase, 如果您不熟悉这个操作，请查看[教程](http://blog.csdn.net/zhi_heart/article/details/48656467)**




## 参考

消息原文:  
<http://bobao.360.cn/news/detail/4263.html>  

linux 禁止帐号密码验证 使用key验证方式登录SSH:  
<http://blog.csdn.net/zhi_heart/article/details/48656467>

