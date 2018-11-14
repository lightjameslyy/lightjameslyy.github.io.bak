---
layout: post
title: "file compression on Unix and Linux"
description: ""
date: 2016-10-24 13:56:10
category: linux
tags: [compress, linux, unix]
---
{% include JB/setup %}

# 1. gzip Compression

​	Typically, `gzip` files are sotred with a `.gz` extension. 

## 1.1. Compress files with `gzip` :

```shell
gzip sourcefile
```

​	This wil compress the file and change the name to `sourcefile.gz`.

## 1.2. Recursively compress an entire directory

```shell
gzip -r directory1
```

## 1.3. list info of the compressed file

```shell
gzip -l test.gz
```

## 1.4. Adjust the compression optimization

​	From `-1`(--fast) to `-9`(--best):

```shell
gzip -9 sourcefile
```

## 1.5. Decompress a `.gz` file

```shell
gzip -d test.gz
```

​	or

```shell
gunzip test.gz
```



# 2. bzip2 Compression

​	Files compressed with `bzip2` are generally given a `.bz2` file extension.

## 2.1. Compress files with `bz2`

```shell
bzip2 testfile
```

​	This will compress the file and give it the name `testfile.bz2`.

## 2.2. Numbered flags (different from that of `gzip`)

​	The number represents the block size that utility manages to implement its compression.

```shell
bzip2 -9 testfile
```

​	The default behavior is the `-9` flag.

## 2.3. Decompress a `.bz2` file

```shell
bzip2 -d testfile.bz2
```



# 3. xz Compression

## 3.1. Compress files with `xz`

```shell
xz testfile
```

​	This will process the file and produce a file called `file.xz`.

## 3.2. List statistics about the compression of the file

```shell
xz -l testfile.xz
```

## 3.3. Decompress a `.xz` file

```shell
xz -d testfile.xz
```



# 4. Using tar archiving with compression

## 4.1. Using tar with gzip

### 4.1.1. compress

```shell
tar czvf test.tar.gz directory1
```

### 4.1.2. peek inside

```shell
tar tzvf test.tar.gz
```

### 4.1.3. decompress

```shell
tar xzvf test.tar.gz
```

## 4.2. Using tar with bzip2

​	To use archiving with `bzip2`, you can replace the `-z` flag, which is `gzip`-specific, with the `-j` flag.

### 4.2.1. compress 

```shell
tar cjvf test.tar.bz2 directory1
```

### 4.2.2. peek inside

```shell
tar tjvf test.tar.bz2
```

### 4.2.3. decompress

```shell
tar xjvf teat.tar.bz2
```

## 4.3. Using tar with xz

​	Any remotely recent versions of `tar` have added similar functionality for `xz` compression. These follow the exact same format using the `-J` flag.

### 4.3.1. compress

```shell
tar cJvf test.tar.xz directory1
```

### 4.3.2. peek inside

```shell
tar tJvf test.tar.xz
```

### 4.3.3. decompress

```shell
tar xJvf test.tar.xz
```

