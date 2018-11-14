---
layout: post
title: "install mesos on mnode"
date: 2017-08-09
description: ""
category: mesos
tags: [mesos]
---

# Table of Contents

1.  [plan](#org7f04573)
2.  [prerequisites](#org5678f3a)
    1.  [关闭防火墙(on all nodes)](#org0b461dd)
    2.  [ssh免密登录(on all nodes)](#org9a15886)
    3.  [如果之前装过mesos，需要清理一些目录(删除或修改)](#org10d8eae)
3.  [配置master节点(mnode04)](#org7860015)
    1.  [添加mesos的yum源](#orgdddbfdc)
    2.  [安装mesos,marathon,zookeeper](#orgbf95f7c)
    3.  [配置zookeeper](#orgbfd27d1)
    4.  [配置mesos和marathon](#orga34d670)
    5.  [启动mesos,marathon,zookeeper](#org161ab76)
    6.  [检查配置](#orga62e6fe)
4.  [配置slave节点(mnode01, mnode02, mnode04)](#org895e479)
    1.  [添加mesos的yum源并安装mesos(mnode01, mnode02)](#org4b9687d)
    2.  [配置slave和master信息](#org8872f19)
    3.  [启动slave](#org476cb4b)
5.  [验证安装](#org0f26d27)
    1.  [web ui](#org7d58e30)
    2.  [测试](#orgd5d58f4)



<a id="org7f04573"></a>

# plan

-   available nodes:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-right" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">hostname</th>
<th scope="col" class="org-right">ip address</th>
<th scope="col" class="org-left">status</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">mnode01</td>
<td class="org-right">10.2.152.21</td>
<td class="org-left">slave</td>
</tr>


<tr>
<td class="org-left">mnode02</td>
<td class="org-right">10.2.152.22</td>
<td class="org-left">slave</td>
</tr>


<tr>
<td class="org-left">mnode04</td>
<td class="org-right">10.2.152.24</td>
<td class="org-left">master & slave</td>
</tr>
</tbody>
</table>


<a id="org5678f3a"></a>

# prerequisites


<a id="org0b461dd"></a>

## 关闭防火墙(on all nodes)

    systemctl stop firewalld && systemctl disable firewalld


<a id="org9a15886"></a>

## ssh免密登录(on all nodes)

-   mnode01
    
        ssh-keygen -t rsa
        ssh-copy-id -i ~/.ssh/id_rsa.pub mnode02
        ssh-copy-id -i ~/.ssh/id_rsa.pub mnode04
-   mnode02
    
        ssh-keygen -t rsa
        ssh-copy-id -i ~/.ssh/id_rsa.pub mnode01
        ssh-copy-id -i ~/.ssh/id_rsa.pub mnode04
-   mnode04
    
        ssh-keygen -t rsa
        ssh-copy-id -i ~/.ssh/id_rsa.pub mnode01
        ssh-copy-id -i ~/.ssh/id_rsa.pub mnode02


<a id="org10d8eae"></a>

## 如果之前装过mesos，需要清理一些目录(删除或修改)

    /var/lib/mesos/
    /var/lib/zookeeper/
    /etc/mesos*/
    /etc/zookeeper/
    /etc/marathon/


<a id="org7860015"></a>

# 配置master节点(mnode04)


<a id="orgdddbfdc"></a>

## 添加mesos的yum源

    rpm -Uvh http://repos.mesosphere.io/el/7/noarch/RPMS/mesosphere-el-repo-7-3.noarch.rpm 


<a id="orgbf95f7c"></a>

## 安装mesos,marathon,zookeeper

    yum -y install mesos marathon mesosphere-zookeeper


<a id="orgbfd27d1"></a>

## 配置zookeeper

    echo 4 > /var/lib/zookeeper/myid
    vim /etc/zookeeper/conf/zoo.cfg
    # 在最后添加 
    # server.4 = 10.2.152.24:2888:3888
    # 2888端口用于集群成员的信息交换
    # 3888端口是在leader挂掉时用来选举新的leader用
    vim /etc/mesos/zk
    # 内容为：
    # zk://10.2.152.24:2181/mesos
    # 设置quorum的值（master节点数目除以2向上取整）
    echo 1 > /etc/mesos-master/quorum


<a id="orga34d670"></a>

## 配置mesos和marathon

    mkdir -p /etc/marathon/conf
    echo 10.2.152.24 > /etc/mesos-master/hostname
    echo 10.2.152.24 > /etc/marathon/conf/hostname
    cp /etc/mesos/zk /etc/marathon/conf/master
    cp /etc/mesos/zk /etc/marathon/conf/zk
    sed -i 's|mesos|marathon|g' /etc/marathon/conf/zk


<a id="org161ab76"></a>

## 启动mesos,marathon,zookeeper

    systemctl start zookeeper && systemctl start mesos-master && systemctl start marathon


<a id="orga62e6fe"></a>

## 检查配置

-   主要配置内容:
    
        /var/lib/zookeeper/myid
        /etc/zookeeper/conf/zoo.cfg
        /etc/mesos/zk
        /etc/mesos-master/quorum
        /etc/mesos-master/hostname
        /etc/marathon/conf/hostname
        /etc/marathon/conf/master
        /etc/marathon/conf/zk


<a id="org895e479"></a>

# 配置slave节点(mnode01, mnode02, mnode04)


<a id="org4b9687d"></a>

## 添加mesos的yum源并安装mesos(mnode01, mnode02)

    rpm -Uvh http://repos.mesosphere.io/el/7/noarch/RPMS/mesosphere-el-repo-7-3.noarch.rpm 
    yum -y install mesos


<a id="org8872f19"></a>

## 配置slave和master信息

-   mnode01
    
        echo 10.2.152.21 > /etc/mesos-slave/hostname
        vim /etc/mesos/zk
        # 内容编辑为:
        # zk://10.2.152.24:2181/mesos
-   mnode02
    
        echo 10.2.152.22 > /etc/mesos-slave/hostname
        vim /etc/mesos/zk
        # 内容编辑为:
        # zk://10.2.152.24:2181/mesos
-   mnode04
    
        echo 10.2.152.24 > /etc/mesos-slave/hostname


<a id="org476cb4b"></a>

## 启动slave

-   mnode01, mnode02 and mnode04
    
        systemctl start mesos-slave


<a id="org0f26d27"></a>

# 验证安装


<a id="org7d58e30"></a>

## web ui

-   mesos的管理页面: <http://10.2.152.24:5050>
-   marathon的管理页面: <http://10.2.152.24:8080>


<a id="orgd5d58f4"></a>

## 测试

-   on mnode04
    
        mesos-execute --master="10.2.152.24:5050" --name="cluster-test" --command="sleep 40"
    
    mesos的管理页面中会显示

