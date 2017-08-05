+++
author = "admin"
date = "2017-08-03T10:01:17+08:00"
draft = false
tags = ["Asp","Login","IP","异地登陆","Ajax"]
topics = ["ASP","IIS","Windows","Ajax"]
keywords = ["asp","iis","异地登陆","IP限制","Ajax","XMLHTTP"]
title = "asp 限制多IP登录"
type = "post"
url = "/2017/08/03/asp_off-site-landing-warning.html"
description = "Asp，限制不同IP不能同时登陆,"
+++


## 目的

**限制同一账号多IP登录**

## 原理

* 前端不断发送Ajax请求后端ASP，每隔几秒钟更新一次登陆请求。
* 后端记录登陆IP和最后登录时间。
* 如发现登录IP与最后登录IP不同，则登陆失败。
* 为了防止请求被缓存, 在请求中加随机数。
* 需要注意的是NAT环境下（网吧或者企业学校等公用出口）, 使用这个代码会导致其他用户登陆失败

## 代码

ajax_update.js
```
//author :x@shellpub.com
//website:www.shellpub.com
function makeRequest() {
    var guid = rnd();
    //记住给个随机数，不然的话有缓存
    var url = "updateLogin.asp";
    createXMLHttpRequest();
    xmlHttp.onreadystatechange = handleRefresh;
    xmlHttp.open("GET", url, false);
    xmlHttp.send(null);
}
//创建xmlHttp
var xmlHttp;
function createXMLHttpRequest() {
    if (window.ActiveXObject) {
        xmlHttp = new ActiveXObject("Microsoft.XMLHTTP");
    }
    else if (window.XMLHttpRequest) {
        xmlHttp = new XMLHttpRequest();
    }
}
//返回信息
function handleRefresh() {
    if (xmlHttp.readyState == 4) {
        if (xmlHttp.status == 200) {
            if (xmlHttp.responseText == "") {
                //alert('登录超时，帐户注销，请重新登录...');
                //window.parent.document.location = "index.asp";
            }
                setTimeout("makeRequest()", 30000);   
        }
    }
}
//创建随机数
rnd.today = new Date();
rnd.seed = rnd.today.getTime();
function rnd() {
    rnd.seed = (rnd.seed * 9301 + 49297) % 233280;
    return rnd.seed / (233280.0);
}
function rand(number) {
    return Math.ceil(rnd() * number);
}
var s2 = setTimeout("makeRequest()", 100);

//updatelogin.asp
<!--#include virtual="function.asp"-->
<%
On Error Resume Next
response.Charset  = "euc-kr"

if session("userid") = "" Then
     'Response.Redirect "index.asp"
     Response.End()
else
     vuserid = Session("userid")
     vip     = Request.serverVariables("REMOTE_HOST")
     set memdb=getServerDB()
     sql = "update member set Last_login=getdate() ,Ip='"&vip&"' WHERE u_id = '"&vuserid&"'"
     memdb.execute(sql)

     memdb.close
     set memdb=nothing
end if
```

更新登陆后端ASP代码，updatelogin.asp。
```
'author :x@shellpub.com
'website:www.shellpub.com
<!--#include virtual="function.asp"-->
<%
On Error Resume Next
response.Charset  = "euc-kr"

if session("userid") = "" Then
 'Response.Redirect "index.asp"
 Response.End()
else
 vuserid = Session("userid")
 vip = Request.serverVariables("REMOTE_HOST")
 set memdb=getServerDB()
 sql = "update member set Last_login=getdate() ,Ip='"&vip&"' WHERE u_id = '"&vuserid&"'"
 memdb.execute(sql)

 memdb.close
 set memdb=nothing
end if

%>
```

检查登陆状态，checklogin.asp
```
<!--#include virtual="function.asp"-->
<%
'author :x@shellpub.com
'website:www.shellpub.com
On Error Resume Next
response.Charset  = "euc-kr"
maxTime = 30
function checkLogin(userid)
     isLogin = False
     vip     = Request.serverVariables("REMOTE_HOST")
     set memdb=getServerDB()
     sql = "select ip,Last_login from  member  WHERE u_id = '"&userid&"'"
     set mRs = memdb.execute(sql)
     Oip = mRs("ip")
     oTime =mRs("Last_login")
     'Response.Write "oip:" & Oip & "nip:" & vip
     if trim(vip)<>trim(Oip) and DateDiff("s",oTime,now()) < maxTime then
          'Response.Write "<script>alert('is Login');history.go(-1);<script>"
          'Response.End()
          isLogin =True
     end if
     memdb.close
     set memdb=nothing
     checkLogin = isLogin
end function
%>
```
