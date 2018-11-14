---
layout: post
title: "通过一个小测试简单理解http的request和response"
date: 2018-11-13 11:26:00 +0800
category: network
tags: [http]
typora-root-url: ..
---

通俗讲 HTTP 协议就是在网络上传输（发布和接受）HTML 的协议，用于浏览器和服务器的通信。

下面进行一个小测试：

* 客户端：MacBook Pro（192.168.0.103）的 Chrome 浏览器。

* 服务端：Windows（192.168.0.105）上的 TCP 调试工具。

## 步骤

1. 服务器要先开启，工作模式为：「TCP 服务器」，端口设置为：「8888」。

2. 浏览器地址栏输入：「192.168.0.105:8888」。

3. 服务端接收到请求：

   ```
   GET / HTTP/1.1
   Host: 192.168.0.105:8888
   Connection: keep-alive
   Upgrade-Insecure-Requests: 1
   User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/70.0.3538.102 Safari/537.36
   Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8
   Accept-Encoding: gzip, deflate
   Accept-Language: zh-CN,zh;q=0.9
   ```

4. 在服务端的发送信息窗口输入：

   ```
   HTTP/1.1 200 ok
   
   <h1>Hello World</h1>
   ```

5. 客户端显示如下页面：

   ![http_response](/assets/images/2018-11-14_http_reponse.jpg)