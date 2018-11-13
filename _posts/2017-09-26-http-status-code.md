---
layout: posts
title: "http status code"
date: 2017-09-26
description: ""
category: network
tags: [http]
---
# Table of Contents

1.  [1xx Informational](#orgdb6c445)
    1.  [100 Continue](#orgb9dcf81)
    2.  [101 Switching Protocols](#orge0d8d28)
2.  [2xx Successful](#orgecf7404)
    1.  [200 Ok](#org606ca38)
    2.  [201 Created](#orgd6ffb22)
    3.  [202 Accepted](#org13160dc)
    4.  [203 Non-Authoritative Information](#orgace1abc)
    5.  [204 No Content](#org4556cc6)
    6.  [205 Reset Content](#org3a8327d)
    7.  [206 Partial Content](#orgc5ddb99)
3.  [3xx Redirection](#org9994a7d)
    1.  [300 Multiple Choices](#org4506692)
    2.  [301 Moved Permanently](#orgf62bdac)
    3.  [302 Found](#orgc7b8cb8)
    4.  [303 See Other](#org1a97507)
    5.  [304 Not Modified](#org9b969b3)
    6.  [305 Use Proxy](#orgf42b3c7)
    7.  [307 Temporary Redirect](#org4cc18f1)
    8.  [308 Permanent Redirect](#org48d512f)
4.  [4xx Client Error](#org2418bc2)
    1.  [400 Bad Request](#org581d045)
    2.  [401 Unauthorized](#org0a3291d)
    3.  [402 Payment Required](#orge2908b3)
    4.  [403 Forbidden](#org00017a1)
    5.  [404 Not Found](#org897f56a)
    6.  [405 Method Not Allowed](#orgdeb5978)
    7.  [406 Not Acceptable](#org77183d4)
    8.  [407 Proxy Authentication Required](#org3d4b178)
    9.  [408 Request Timeout](#orga7cefa3)
    10. [409 Conflict](#orga85fa77)
    11. [410 Gone](#org6d721e9)
    12. [411 Length Required](#orgb8e5459)
    13. [412 Precondition Failed](#orgdb4f3b8)
    14. [413 Request Entity Too Large](#org541c6ab)
    15. [414 Request-URI Too Long](#org21fafb3)
    16. [415 Unsupported Media Type](#org9ff1c64)
    17. [416 Requested Range Not Satisfiable](#org0eebf6d)
    18. [417 Expectation Failed](#orge5414a5)
5.  [5xx Server Error](#org905dbce)
    1.  [500 Internal Server Error](#orgae5db54)
    2.  [501 Not Implemented](#orgea1c7b5)
    3.  [502 Bad Gateway](#org1bccc9f)
    4.  [503 Service Unavailable](#org5618fbf)
    5.  [504 Gateway Timeout](#org2bc4e39)
    6.  [505 HTTP Version Not Supported](#orgdd83e07)



<a id="orgdb6c445"></a>

# 1xx Informational

代表请求已被接受，需要继续处理。


<a id="orgb9dcf81"></a>

## 100 Continue

服务器已经接收到请求头，并且客户端应继续发送请求主体，或者如果请求已经完成，忽略这个响应。


<a id="orge0d8d28"></a>

## 101 Switching Protocols

服务器已经理解了客户端的请求，并将通过Upgrade消息头通知客户端采用不同的协议来完成这个请求。


<a id="orgecf7404"></a>

# 2xx Successful


<a id="org606ca38"></a>

## 200 Ok

请求已成功，请求所希望的响应头或数据体将随此响应返回。


<a id="orgd6ffb22"></a>

## 201 Created

请求已经被实现，而且有一个新的资源已经依据请求的需要而创建，且其URI已经随Location头信息返回。


<a id="org13160dc"></a>

## 202 Accepted

服务器已接受请求，但尚未处理。


<a id="orgace1abc"></a>

## 203 Non-Authoritative Information


<a id="org4556cc6"></a>

## 204 No Content

服务器成功处理了请求，没有返回任何内容。


<a id="org3a8327d"></a>

## 205 Reset Content

服务器成功处理了请求，但没有返回任何内容。与204响应不同，此响应要求请求者重置文档视图。


<a id="orgc5ddb99"></a>

## 206 Partial Content

服务器已经成功处理了部分GET请求。


<a id="org9994a7d"></a>

# 3xx Redirection


<a id="org4506692"></a>

## 300 Multiple Choices

被请求的资源有一系列可供选择的回馈信息，每个都有自己特定的地址和浏览器驱动的商议信息。用户或浏览器能够自行选择一个首选的地址进行重定向。


<a id="orgf62bdac"></a>

## 301 Moved Permanently

被请求的资源已永久移动到新位置，并且将来任何对此资源的引用都应该使用本响应返回的若干个URI之一。


<a id="orgc7b8cb8"></a>

## 302 Found

要求客户端执行临时重定向。


<a id="org1a97507"></a>

## 303 See Other

对应当前请求的响应可以在另一个URI上被找到。


<a id="org9b969b3"></a>

## 304 Not Modified

表示资源未被修改，因为请求头指定的版本If-Modified-Since或If-None-Match。在这种情况下，由于客户端仍然具有以前下载的副本，因此不需要重新传输资源。


<a id="orgf42b3c7"></a>

## 305 Use Proxy

被请求的资源必须通过指定的代理才能被访问。


<a id="org4cc18f1"></a>

## 307 Temporary Redirect

在这种情况下，请求应该与另一个URI重复，但后续的请求应仍使用原始的URI。


<a id="org48d512f"></a>

## 308 Permanent Redirect

请求和所有将来的请求应该使用另一个URI重复。307和308重复302和301的行为，但不允许HTTP方法更改。


<a id="org2418bc2"></a>

# 4xx Client Error


<a id="org581d045"></a>

## 400 Bad Request

由于明显的客户端错误（例如，格式错误的请求语法，太大的大小，无效的请求消息或欺骗性路由请求），服务器不能或不会处理该请求。


<a id="org0a3291d"></a>

## 401 Unauthorized

用户没有必要的凭据。


<a id="orge2908b3"></a>

## 402 Payment Required


<a id="org00017a1"></a>

## 403 Forbidden

服务器已经理解请求，但是拒绝执行它。


<a id="org897f56a"></a>

## 404 Not Found

请求失败，请求所希望得到的资源未被在服务器上发现，但允许用户的后续请求。


<a id="orgdeb5978"></a>

## 405 Method Not Allowed

请求行中指定的请求方法不能被用于请求相应的资源。


<a id="org77183d4"></a>

## 406 Not Acceptable

请求的资源的内容特性无法满足请求头中的条件，因而无法生成响应实体，该请求不可接受。


<a id="org3d4b178"></a>

## 407 Proxy Authentication Required

客户端必须在代理服务器上进行身份验证。


<a id="orga7cefa3"></a>

## 408 Request Timeout

请求超时。


<a id="orga85fa77"></a>

## 409 Conflict

表示因为请求存在冲突无法处理该请求，例如多个同步更新之间的编辑冲突。


<a id="org6d721e9"></a>

## 410 Gone

表示所请求的资源不再可用，将不再可用。


<a id="orgb8e5459"></a>

## 411 Length Required

服务器拒绝在没有定义Content-Length头的情况下接受请求。


<a id="orgdb4f3b8"></a>

## 412 Precondition Failed

服务器在验证在请求的头字段中给出先决条件时，没能满足其中的一个或多个。


<a id="org541c6ab"></a>

## 413 Request Entity Too Large

服务器拒绝处理当前请求，因为该请求提交的实体数据大小超过了服务器愿意或者能够处理的范围。


<a id="org21fafb3"></a>

## 414 Request-URI Too Long

请求的URI长度超过了服务器能够解释的长度，因此服务器拒绝对该请求提供服务。


<a id="org9ff1c64"></a>

## 415 Unsupported Media Type

对于当前请求的方法和所请求的资源，请求中提交的互联网媒体类型并不是服务器中所支持的格式，因此请求被拒绝。


<a id="org0eebf6d"></a>

## 416 Requested Range Not Satisfiable

客户端已经要求文件的一部分（Byte serving），但服务器不能提供该部分。


<a id="orge5414a5"></a>

## 417 Expectation Failed

在请求头Expect中指定的预期内容无法被服务器满足，或者这个服务器是一个代理服显的证据证明在当前路由的下一个节点上，Expect的内容无法被满足。


<a id="org905dbce"></a>

# 5xx Server Error


<a id="orgae5db54"></a>

## 500 Internal Server Error

服务器遇到了一个未曾预料的状况，导致了它无法完成对请求的处理。


<a id="orgea1c7b5"></a>

## 501 Not Implemented

服务器不支持当前请求所需要的某个功能。


<a id="org1bccc9f"></a>

## 502 Bad Gateway

作为网关或者代理工作的服务器尝试执行请求时，从上游服务器接收到无效的响应。


<a id="org5618fbf"></a>

## 503 Service Unavailable

由于临时的服务器维护或者过载，服务器当前无法处理请求。这个状况是暂时的，并且将在一段时间以后恢复。


<a id="org2bc4e39"></a>

## 504 Gateway Timeout

作为网关或者代理工作的服务器尝试执行请求时，未能及时从上游服务器（URI标识出的服务器，例如HTTP、FTP、LDAP）或者辅助服务器（例如DNS）收到响应。


<a id="orgdd83e07"></a>

## 505 HTTP Version Not Supported

服务器不支持，或者拒绝支持在请求中使用的HTTP版本。

