---
layout: post
title: "sed learning notes"
date: 2017-09-14 23:27:45
description: ""
category: linux
tags: [sed, regular expression, linux]
---

[TOC]

# sed notes

## what is sed?

`sed` is a stream editor. A stream editor is used to perform basic text transformations on an input stream (a file or input from a pipeline). 

## 语法

`sed OPTIONS... [SCRIPT] [INPUTFILE...]`

## 选项

|-----------------------|--------------------------------------|
| 选项                  | 解释                                 |
| --------------------- | ----------------------               |
| -f *script-file*      | 添加*script-file*到命令              |
| -i [*suffix*]         | 就地编辑。*suffix*指定备份文件后缀名 |
| -n/--quiet/ -- slient | slient                               |
| -e *script*           | 添加*script*到命令                   |
|-----------------------|--------------------------------------|

## 基础

- 命令结构：

  *[address[, address]] instruction [argument-list]*

  ### 地址(address)

  类似于awk的范围模式。$表示最后一行。

  ### 指令

|------------------------|---------------------------------------------------------------------------------------------|
| 指令                   | 解释                                                                                        |
| ---------------------- | ----------------------------------------                                                    |
| a (append)             | append text **after** a line                                                                |
| c (change)             | change *lines* with text                                                                    |
| d (delete)             | stop processing the current line, immediately start next cycle                              |
| i (insert)             | insert text **before** a line                                                               |
| N (next without write) | add a newline to the pattern space, then append the next line of input to the pattern space |
| n (next)               | print the pattern space, then replace the pattern space with the next line of input         |
| p (print)              | print the pattern space                                                                     |
| q (quit)               | exit                                                                                        |
| r *filename* (read)    | read text of a file                                                                         |
| s (substitute)         | format: *s/regexp/replacement/[flags]*                                                      |
| w *filename* (write)   | write the pattern space to *filename*                                                       |
|------------------------|---------------------------------------------------------------------------------------------|

  ### 控制结构

|-----------|---------------------------------------|
| 符号      | 解释                                  |
| --------- | --------------------                  |
| ! (NOT)   | not                                   |
| {}        | 将一组指令括起来，用$;$将多条指令隔开 |
| :label    | 标记一个位置，作为跳转目标            |
| b [label] | 无条件转移                            |
| t [label] | 匹配成功则转移                        |
|-----------|---------------------------------------|

  ### 暂存空间

|------|--------------------------------------------------------------|
| 符号 | 解释                                                         |
| ---- | ------------------------------                               |
| g    | 将暂存空间的内容复制到模式空间中，模式空间中原来的内容丢失   |
| G    | 将一个换行符和暂存空间中的内容append到模式空间中             |
| h    | 将模式空间中的内容复制到暂存空间中，暂存空间中原来的内容丢失 |
| H    | 将一个换行符和模式空间中的内容append到暂存空间中             |
| x    | 交换模式空间和暂存空间中的内容                               |
|------|--------------------------------------------------------------|

  ### regular expression extensions

|--------|---------------------------------------------------------------|
| symbol | explanation                                                   |
| ------ | ----------------------------------------                      |
| \w     | any "word" character (字母、数组、下划线)                     |
| \W     | any "non-word" character                                      |
| \b     | a word boundary                                               |
| \B     | every but on a word boundary                                  |
| \s     | whitespace characters (空格、tab、暂存空间和模式空间中的回车) |
| \S     | non-whitespace characters                                     |
| \\<    | beginning of a word                                           |
| \\>    | end of a word                                                 |
| \\`    | start of **pattern space**, different from ^                  |
| \\'    | end of **pattern space**, different from `$`                  |
|--------|---------------------------------------------------------------|

