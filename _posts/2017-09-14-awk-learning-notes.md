---
layout: posts
title: "awk learning notes"
description: ""
date: 2017-09-14 13:25:26
category: linux
tags: [awk, regular expression]
---

# AWK Learning Notes

---

## What is awk?

> An awk program is a sequence of patterns and actions that tell what to look for in the input data and what to do when it's found.

---

## Patterns

### Summary of Patterns

![000001]({{site.url}}/assets/image/000001.png)

### String-Matching Patterns

![000002]({{site.url}}/assets/image/000002.png)

### Regular Expression

![000003]({{site.url}}/assets/image/000003.png)

![000004]({{site.url}}/assets/image/000004.png)

### 转义序列

![000005]({{site.url}}/assets/image/000005.png)

### 模式总结

![000006]({{site.url}}/assets/image/000006.png)

------

## Actions

### statements in actions

![000007]({{site.url}}/assets/image/000007.png)

**注意：`for (expression in array) statements` 中的<u>expression</u>是array的index而不是array的element**

### built-in variables

![000008]({{site.url}}/assets/image/000008.png)

### expressions

![000009]({{site.url}}/assets/image/000009.png)

### built-in arithmetic functions

![000010]({{site.url}}/assets/image/000010.png)

### built-in string functions

![000011]({{site.url}}/assets/image/000011.png)

### expression operators

![000012]({{site.url}}/assets/image/000012.png)

### control-flow statements

![000013]({{site.url}}/assets/image/000013.png)

### 用户自定义函数

```awk
function name(parameter-list) {
  	statements
  	return result
}
```

## getline函数

![000014]({{site.url}}/assets/image/000014.png)

**注：`getline < file`和`getline var < file`可以用在`BEGIN`中进行“预处理”（不会设置NR变量）。**

