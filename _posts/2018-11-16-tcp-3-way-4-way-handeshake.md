---
layout: post
title: TCP 的三次握手和四次挥手
categories: [network, tcp]
description: 记录我对 TCP 的理解和心得
keywords: network, tcp
typora-root-url: ..
---

## 前言

跟 UDP 相比，TCP 是面向连接的、可靠的协议。

两个进程在使用 TCP 传输数据之前必须先使用「三次握手」来建立连接。完成数据交换后，经过「四次挥手」来关闭这个连接。

本文的目的是分析「TCP连接的建立和终止」，可能我的理解是片面的，后续我会不断更新我的理解。

在下面的分析中，我们假设有两个角色：client 和 server。

## 1. 建立连接

### 1.1 直觉

为了建立可靠的连接，就不能像 UDP 那样，消息发送后就撒手不管。<font color="red">通信的双方必须要确认自己发送的消息对方接收到了才行。</font>那么如何做到这一点呢？一种可行的方法是：发送方在发送的数据中加上一个**「标记」**，接收方收到数据后要回送一个**「应答」**，发送方收到接收方的应答后才会认为数据发送成功。

接下来思考一个更加现实的问题：怎样建立 client 和 server 之间的可靠连接呢？

根据上面的分析，自然而然的就想到一种方法：

1. client 跟 server 说：「我要跟你建立连接」；
2. server 回复 client ：「我**准备好了**，来吧」；
3. server 紧接着又问 client：「我准备好了，那你呢？不会放我鸽子吧？」；
4. client 又回复说：「放心吧，我也**准备好了**」。

假设发送数据的时候会给数据加上一个数字 `id` 做为标记，收到标记为 `id+1` 的数据才能确认数据发送成功。所以上面的过程可以这样描述为下图的过程：

1. client 发送一条数据到 server，标记为 10；
2. server 回复一条数据，标记为11，client 收到 11 后就知道 server 准备好了；
3. server 向 client 发送一条数据，标记为 20；
4. client 回复一条数据，标记为 21，server 收到 21 后也知道 client 准备好了。
5. 至此，双方都确认对方已经准备好进行数据传输了，意味着连接建立成功了。

![](/assets/images/2018-11-16_tcp_4_way_connect.png)

在这个过程中，数据「10」和「11」代表的是**请求**，「11」和「21」代表的是**应答**。


### 1.2 TCP 的做法

TCP 建立连接是经过三次握手，而上面是通过四次握手建立连接，能不能少握一次呢？减少一次通信肯定能快一点建立连接。回头再看看，这四次握手有没有多余的呢？

从数据传输方向上来看，**第二次和第三次都是 server 向 client 发送数据**，而且在这之间 server 没有任何其他的数据向 client 传输，那么我们可以将他们合二为一，这样就只剩三次握手了。从四次到三次，提高了数据传输的效率，缩短了建立连接的时间。

这样的话，当 server 将带有请求 11 和应答 20 的数据发送给 client 的时候，client 如何知道 11 和 20 各自的含义呢？其实很简单，给他们取个名字就行了。如下图，用 SYN 标记发送的数据的序号，ACK 用来标记对收到的 SYN 的确认。

![](/assets/images/2018-11-16_tcp_3_way_connect.png)

再来一个更加详细的图（注意图中 connect 函数和 accept 函数何时返回）：

![](/assets/images/2018-11-16_tcp_3_way_connect_1.png)

## 连接终止

TCP 连接终止使用四次挥手，这里假设 client 主动关闭连接。

1. 首先，client 发送 FIN 给 server 说：「我要关闭连接了，不会再接受数据了」；
2. server 回复 client 对 FIN 的 ACK：「好的，我知道了，等我处理完数据我也关闭连接」；
3. server 发送 FIN 给 client：「我也要关闭了，收到消息请回复」；
4. client：「好的，我知道了，你可以关闭了」。

![](/assets/images/2018-11-16_tcp_connect_close.png)

问题又来了，为什么第二次和第三次不能合二为一呢？

虽然第二次和第三次都是 server 向 client 传输数据，但是 TCP 是**全双工**的，一方关闭不影响另一方的数据传输，**在这两次传输之间 server 可能需要继续等待 client 发出的尚未收到的数据或处理之前收到的数据**，如果硬要合到一起，对 client 而言，这个过程可能要阻塞一段时间，性能就会下降。