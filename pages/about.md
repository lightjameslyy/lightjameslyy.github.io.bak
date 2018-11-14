---
layout: page
title: About
description: 学无止境，学以致用
keywords: Liu Tao, lightjameslyy 
comments: true
menu: 关于
permalink: /about/
---

我是刘涛，喜欢闭关修炼，折腾各种IT技术。

我的座右铭是：「学无止境，学以致用」。

我的爱好：编程，摄影，吉他，篮球，羽毛球。

感谢[马壮](https://mazhuang.org)兄弟分享的博客配置，很适合程序员写博客。

## 联系

{% for website in site.data.social %}
* {{ website.sitename }}：[@{{ website.name }}]({{ website.url }})
{% endfor %}

## Skill Keywords

{% for category in site.data.skills %}
### {{ category.name }}
<div class="btn-inline">
{% for keyword in category.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}
