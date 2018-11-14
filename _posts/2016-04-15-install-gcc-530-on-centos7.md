---
layout: post
title: "install gcc 5.3.0 on centos7"
date: 2016-04-15 20:44:44
description: ""
category: compiler
tags: [gcc, centos]
---
{% include JB/setup %}

# 1.Preparations  

* operating system: CentOS 7 64bit
* old gcc: gcc 4.8.2
* source packages: gcc-5.3.0.tar.gz gmp-6.1.0.tar.bz2 mpc-1.0.3.tar.gz mpfr-3.1.3.tar.gz

# 2.Unzip  

change to an appropriate directory (mine is **/usr/local**) and unzip the 4 packages:  
tar -jxvf gmp-6.1.0.tar.bz2  
tar -zxvf mpfr-3.1.3.tar.gz  
tar -zxvf mpc-1.0.3.tar.gz  
tar -zxvf gcc-5.3.0.tar.gz  

# 3.Install  

## 3.1.install gmp  

    > cd /usr/local/gmp-6.1.0
    > ./configure
    > make -j2
    > make install -j2  

NOTICE:   
    (1) If there are errors such as **"Permission denied..."**, you need to switch to super user and repeat the process.  
    (2) The header and library genetated by gmp should already be located under /usr/local/include and /usr/local/lib.

## 3.2.install mpfr  

    > cd /usr/local/mpfr-3.1.3
    > ./configure --with-gmp-include=/usr/local/include --with-gmp-lib=/usr/local/lib
    > make -j2
    > make install -j2

## 3.3.install mpc  

    > cd /usr/local/mpc-1.0.3
    > ./configure
    > make -j2
    > make install -j2
    > export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib

NOTICE:  
    Don't forget to change the environment variable **$LD_LIBRARY_PATH** which is necessary for compiling gcc later.
    
## 3.4.install gcc  

    > cd /usr/local/gcc-5.3.0
    > mkdir build
    > cd build
    > ../configure --prefix=/usr/local/gcc --enable-threads=posix --disable-checking --enable-languages=c,c++ --disable-multilib --with-gmp=/usr/local/lib --with-mpfr=/usr/local/lib --with-mpc=/usr/local/lib
    > make -j2
    > make install -j2

NOTICE:  
while **make**, I have the following errors:
```
...[s-attrtab]... 
...[all-stage1-gcc]...
...[stage1-bubble]...
```
this means you need to add **swap** partition, I made it by editing **/etc/sysctl.conf**  
changing  
```
vm.swappiness = 0
```
to
```
vm.swappiness = 60
```
then restart the operating system, continue from **make -j2**.

# 4.Remove old version  

	> yum remove gcc
	> yum remove gcc-c++ 
	> updatedb

# 5.Link to new version  

    > cd /usr/bin 
    > ln -s /usr/local/gcc/bin/gcc gcc 
    > ln -s /usr/local/gcc/bin/g++ g++
    
# 6.Add man help  

    > vim /etc/man_db.conf  
add entry:
```
MANDATORY_MANPATH                       /usr/local/gcc/share/man
```
save and exit.

# 7.Check

    > gcc -v

see whether the version is 5.3.0.


