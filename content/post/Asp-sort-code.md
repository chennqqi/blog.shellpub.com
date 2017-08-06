+++
author = "admin"
date = "2017-08-05T11:01:15+08:00"
draft = false
tags = ["Asp","排序"]
topics = ["ASP","IIS","Windows"]
keywords = ["asp","iis","排序"]
title = "Asp生成按照字段排序代码"
type = "post"
url = "/2017/08/05/asp_sort-code.html"
description = "Asp生成按照字段排序代码"
+++

```
//author :x@shellpub.com
//website:www.shellpub.com
function subject_sort_link(sod,sord,sst,flag,sType,svalue,nPage)
          q1 = "sod=" & sod
          if flag = "asc" Then
               q2="sst=asc"
               if sod=sord then
                    if sst = "asc" then
                         q2 = "sst=desc"
                    end if
               end if
          else
               q2 = "sst=desc"
               if sod=sord then
                    if sst = "desc" then
                         q2 = "sst=asc "
                    end if
               end if
          end if
          response.Write "<a href=list.asp?nPage=" & nPage & "&sType=" & sType & "&sValue="&keyword&"&"&q1&"&"&q2&">"
     end function

函数调用 可以生成连接 create_time 为排序的数据库字段
subject_sort_link("create_time",sod,sst,"desc",sType,sValue,nPage)

在组装sql语句的时候,如果为空的时候，设置默认的排序规则。
if sst = "" Then
       sst = " desc"
  end if
  if sod <> ""  Then
       sord = getDatabase(sod) & "." & sod & " "
  else
       sord = " m.idx "
  end if
```