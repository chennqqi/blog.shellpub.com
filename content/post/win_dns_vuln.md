+++
draft = false
author = "晴天@河马"
date = 2020-07-17T13:45:36+08:00
description = ""
keywords = [ "windows漏洞" ]
title = 'Windows DNS Server"蠕虫级"漏洞通知，请马上升级'
topics = ["漏洞通知"]
tags = ["漏洞","windows", "dns","蠕虫","补丁"]
type = "post"
url = "/2020/07/17/windows_DNS_vuln.html"
+++

# Windows DNS Server "蠕虫级"漏洞通知，请马上升级

> 某些情形下，企业DNS Server和域控处于内网同一台服务器中，SIGRed漏洞影响的组件dns.exe是以System权限运行，目前网络上已有PoC公开，建议用户尽快升级，避免由于该漏洞导致域控沦陷。

## 简介

微软公司在本月的安全补丁推送中修复了一个长达17年的“蠕虫级”漏洞。据国外研究机构checkpoint描述成功利用SIGRed漏洞可以达到远程提权的效果。其影响几乎市面上主流的所有Windows Server版本（Windows Server 2008 、2012、2016、2019以及之后的Windows Server, version 1903、1909、2004）。目前网络已经有公开的dns拒绝服务PoC代码，请务必重视！

## 漏洞原理简述

在Windows系统中，DNS客户端主要实现在dnsspi.dll中，而DNS服务端是由dns.exe负责响应和处理请求。而SIGRed漏洞就发生在`dns.exe!SigWireRead`函数。

可以看到`RR_AllocateEx`分配内存是通过16位寄存器`cx`，如果我们这里可以控制其第一个参数大于0xffff，那么就会产生整数溢出，紧接会触发到后面的`memcpy`导致崩溃。

![](/images/sigdns.jpg)

## 触发漏洞

引用checkpoint的研究，利用`DNS Pointer Compression `。这里主要是一种类似指针指向的压缩编码方式。

`c00c`其中`0xc0`是引用这个packet内部值的标识。`0x0c`是基于dns header偏移位置，这里指向 (<size><value>) chain。也就是下图划线的部分。其中`08`是size，`research`是value。如果我们修改`0x0c`为`0x0d`，那么size就变成`0x72`,这就是导致`unCompression `数据长度发生变化，触发整数溢出。



![](/images/image-9.png)



## 处置建议

- 升级微软官方最新补丁

- 临时处置建议

  通过设置注册表临时缓解，然后重启dns服务

  ```
    HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\DNS\Parameters 
    DWORD = TcpReceivePacketSize 
    Value = 0xFF00
  ```

  如之后升级补丁，删除` HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\DNS\Parameters`即可。

## 参考

https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2020-1350

https://research.checkpoint.com/2020/resolving-your-way-into-domain-admin-exploiting-a-17-year-old-bug-in-windows-dns-servers/

## 关注我们

![](images/qrcode_gh_d110440c4890_1.jpg)