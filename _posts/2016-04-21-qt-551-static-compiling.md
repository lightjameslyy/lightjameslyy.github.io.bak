---
layout: post
title: "Qt 5.5.1 static compiling"
date: 2016-04-21 23:16:17
description: ""
category: compiler
tags: [Qt, compiler]
---
{% include JB/setup %}

# 1. Problem  

进行Qt开发时，程序写好后在本机能运行，但是打包的.exe文件在没有安装Qt的机器上不能运行。原因：因为采用了动态编译，一起打包的dll文件都是动态库。解决方法是采用静态编译。  

# 2. Solution  

言归正传，下面就是我静态编译Qt的过程（我使用的版本是Qt5.5.1）。  

1) 确保已经安装了Qt 5.5.1。  
2) 下载Qt 5.5.1的源码：http://download.qt.io/archive/qt/5.5/5.5.1/single/ 。   
3) 安装python。  
4) 把源码解压到C盘（我的路径是C:\qt-everywhere-opensource-src-5.5.1）。编辑C:\qt-everywhere-opensource-src-5.5.1\qtbase\mkspecs\win32-g++\qmake.conf，找到QMAKE_LFLAGS和QMAKE_LFLAGS_DLL，后面赋值为 –static：
```
QMAKE_LFLAGS = -static  
QMAKE_LFLAGS_DLL = -static
```
保存，退出。  
5) 打开终端：windows键==>all apps==>Qt 5.5.1==>Qt 5.5.1 for Desktop (MinGW 4.9.2 32 bit)，切换路径到C:\qt-everywhere-opensource-src-5.5.1。  
6) configure： 
```
configure -confirm-license -opensource -platform win32-g++ -release -static -ltcg -prefix "C:\Qtstatic" -qt-sql-sqlite -qt-sql-odbc -plugin-sql-sqlite -plugin-sql-odbc -qt-zlib -qt-libpng -qt-libjpeg -opengl desktop -no-qml-debug -nomake tests -nomake examples -skip qtwebkit -qt-pcre -no-compile-examples  
```
（C:\Qtstatic为安装路径，可自定义）  
7) mingw32-make  
8) mingw32-make install  
***注：make和make install 需要的时间较多，可能要3到4个小时***  
9) 添加编译选项 
	打开QtCreator==>Tools==>options==>build&run==>QtVersions==>add==>选择***C:\Qtstatic\bin\qmake.exe***==>apply  
10）done^_^


