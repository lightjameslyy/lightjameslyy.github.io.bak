---
layout: post
title: Windows 10 交换 Caps 和左 Ctrl 按键
categories: windows
description: 
keywords: windows
typora-root-url: ..
---

之前一直使用 MacBook Pro 办公，而且读研的时候折腾过一阵 Emacs。出于按键习惯的原因，我把 Caps 按键和 Ctrl 按键交换了，感觉效率确实高了一些。久而久之就习惯了这种按键方式。

在 MacBook Pro 上更换的方法是：

1. 「系统偏好设置」==>「键盘」==>「修饰键」（右下角）；
2. 大写锁定键：选择 Control；Control 键：选择大写锁定键。

后来我入手了梦寐以求的 FILCO 出品的 [Majestouch MINILA](https://item.jd.com/3376782.html)，不仅手感好，还支持 DIP 开关，掰一下开关就实现 Caps 键和 Ctrl 键的交换了！

老板人好，上个月给配了一台 Surface Laptop，16 GB 内存加 512 GB SSD。笔记本的配置还是比较爽的，但是按键不知道咋改……像我这种有强迫症、爱折腾的程序猿怎么能忍，于是我习惯性的去找 Google 大哥帮忙。找到一个感觉很原始但是确实有效的方法（on Windows 10）：

1. 按键：「Win + R」;

2. 输入：「regedit」，打开注册表；

3. 依次进入：HKEY_LOCAL_MACHINE ==> System ==> CurrentControlSet ==> Control ==> KeyBoard Layout；

4. 右击「KeyBoard Layout」，依次选择「新建」=> 「二进制值」；

5. 将「新值 #1」重命名为 Scancode Map；

6. 右击 「Scancode Map」，选择「修改」；

7. 输入如下值并保存：

   ![Scancode Map](/assets/images/2018-11-14_scancode_map.jpg)

8. 重启生效。