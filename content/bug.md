+++
author = "admin@shellpub.com"
date = "2018-04-10T15:31:21+08:00"
keywords = ["河马常见问题", "河马崩溃"]
title = "河马查杀BUG跟踪"
tags = ["bug"]
sidemenu = "true"
+++


id， bug编号
状态，是否已修复
计划, 修复计划
范围，受影响版本范围

<table>
  <tr>
    <th width=10%, bgcolor=yellow >id</th>
    <th width=10%, bgcolor=yellow>状态</th>
    <th width=10%, bgcolor=yellow>范围</th>
    <th width=20%, bgcolor=yellow>计划</th>
    <th width="60%", bgcolor=yellow>描述</th>
  </tr>
  <tr>
    <td> 1 </td>
    <td> 已修复 </td>
    <td> 小于1.3.2 </td>
    <td> 已修复(>=1.3.2) </td>
    <td> 请求dns崩溃参考https://yq.aliyun.com/articles/238940</td>
  </tr>
  <tr>
    <td> 2 </td>
    <td> 未修复 </td>
    <td> 所有版本 </td>
    <td> 修复中 </td>
    <td> linux内核版本>4.4时，扫描时会崩溃 </td>
  </tr>
</table>