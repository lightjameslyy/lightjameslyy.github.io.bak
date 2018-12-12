---
layout: post
title: jekyll blog series
categories: [blog, jekyll]
description: about jekyll
keywords: blog, jekyll
typora-root-url: ..
---

本文参考 Youtube 频道：[代码真香](https://www.youtube.com/watch?v=Zt_QzSbyDcw&t=0s&index=2&list=PLK2w-tGRdrj7vzX7Y-GqKPb2QPrHCYZY1)

## jekyll 快速入门

Jekyll 是一个静态站点生成器，它是 GitHub 创始人创造的，被非常多的极客使用，阮一峰的博客也是用它搭建。Jekyll 会根据网页源码生成静态文件，包括 html，css，js等。它提供了模板、变量、插件等功能，所以实际上可以用来编写整个网站。但是和WordPress又有很大的不同，原因是jekyll只是一个生成静态网页的工具，不需要数据库支持。它使用 Ruby 编写，通过 Markdown 和 Liquid 模板生成内容。

其他主流的博客搭建方式：

* WordPress
* typecho
* Tale
* Hexo
* Hugo

特点：

* 简单
* 静态
* 对 Github 支持友好
* 博客支持

规划：

1. 快速在本地搭建博客
2. 将博客部署到可访问的域名
3. 常用插件和配置
4. Liquid 模板语法



### 在本地搭建博客

#### 1. 安装（on MacOS）

```shell
brew install ruby
sudo gem install jekyll
sudo gem install jekyll bundler
```

**Gem 安装不上或很慢怎么办？**

更换 gem 的源：

```shell
gem sources --add https://gems.ruby-china.org/ --remove https://rubygems.org/
```

#### 2. 创建博客

创建博客目录：

```shell
jekyll new myblog
cd myblog
```

安装依赖：

```shell
sudo bundle install
bundle exec jekyll serve
```

运行本地博客服务：

```shell

```

默认从 127.0.0.1:4000 访问。

一些文件和目录的作用：

* `_config.yml`：是最重要的配置文件。
* `_post`：展示的博客文章。
* `_drafts`：草稿，不会展示。
* `_site`：生成的静态网站内容。

#### 3. 使用别人的主题

1. 克隆主题。
2. 安装依赖。
3. 更换文章。
4. 运行和部署。