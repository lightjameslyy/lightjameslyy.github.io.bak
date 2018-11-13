---
layout: single
title: "awk learning notes"
description: ""
date: 2017-09-14 13:25:26
category: linux
tags: [awk, regular expression]
typora-root-url: ..
---

# AWK Learning Notes

---

## What is awk?

> An awk program is a sequence of patterns and actions that tell what to look for in the input data and what to do when it's found.

---

## Patterns

### Summary of Patterns

<img src="/assets/image/000001.png" alt="000001" width="80%">

### String-Matching Patterns

<img src="/assets/image/000002.png" alt="000002" width="80%">

### Regular Expression

<img src="/assets/image/000003.png" alt="000003" width="80%">

<img src="/assets/image/000004.png" alt="000004" width="80%">

### 转义序列

<img src="/assets/image/000005.png" alt="000005" width="80%">

### 模式总结

<img src="/assets/image/000006.png" alt="000006" width="80%">

------

## Actions

### statements in actions

<img src="/assets/image/000007.png" alt="000007" width="80%">

**注意：`for (expression in array) statements` 中的<u>expression</u>是array的index而不是array的element**

### built-in variables

<img src="/assets/image/000008.png" alt="000008" width="80%">

### expressions

<img src="/assets/image/000009.png" alt="000009" width="80%">

### built-in arithmetic functions

<img src="/assets/image/000010.png" alt="000010" width="80%">

### built-in string functions

<img src="/assets/image/000011.png" alt="000011" width="80%">

### expression operators

<img src="/assets/image/000012.png" alt="000012" width="80%">

### control-flow statements

<img src="/assets/image/000013.png" alt="000013" width="80%">

### 用户自定义函数

```awk
function name(parameter-list) {
  	statements
  	return result
}
```

## getline函数

<img src="/assets/image/000014.png" alt="000014" width="80%">

**注：`getline < file`和`getline var < file`可以用在`BEGIN`中进行“预处理”（不会设置NR变量）。**

