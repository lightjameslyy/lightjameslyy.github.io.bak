---
layout: post
title: mount nfs on windows 10
categories: [nfs, windows]
description: windows as nfs client, centos as nfs server.
keywords: nfs, windows
typora-root-url: ..
---

## 在 Windows 10 上挂载 nfs

### 环境

* nfs server: Linux（Centos 7）
* nfs client: Windows 10

### 准备工作

* nfs server 已经部署好
* 挂载后可能没有修改目录的权限，这是因为 GID 和 UID 设置不对，详见 http://dovidenko.com/2017/505/nfs-centos-7-windows-10-network-shares.html
* 运行「命令提示符」时要以管理员权限运行

### Windows 10 上的配置步骤

1. 按「Win+R」输入「OptionalFeatures」，勾选「NFS服务」中的「NFS客户端」。

   ![](/assets/images/2018-12-14_optionalfeatures.jpg)

   ![](/assets/images/2018-12-14_select_nfs_client.jpg)

2. 查看 nfs server 共享的目录

   ```shell
   showmount -e <nfs_server_ip>
   ```

   ![](/assets/images/2018-12-14_showmount.jpg)

3. 挂载（以匿名模式）

```shell
mount \\<nfs_server_ip>\<nfs_dir> <local_nfs_volume>
```

![](/assets/images/2018-12-14_mount.jpg)

4. 卸载

   ```shell
   umount <local_nfs_volume>
   ```

   ![](/assets/images/2018-12-14_umount.jpg)