---
title: Hexo博客搭建之SSL证书突然过期解决办法 | coding 3个月域名证书过期申请失败解决方案
iscopyright: true
comments: true
lang: cn
date: 2019-11-11 18:32:26
updated: 2019-11-11 18:32:26
abbrlink:
author:
tags:
categories:
---


# 前沿（吹牛逼）
每天码搬砖中~~

突然有一天想去看看自己网站 欣赏一下自己作品 

打开


# 问题
[!](http://img.0x96m.com/hexo/coding_err.jpg)
自习查看一遍后


# 解决方案
在同时部署 github 和 coding 后 第一次在coding申请ssl 证书 成功了 

但是 在三个月后的今天 我访问我的网站 突然说证书不可用 搜寻一番后 发现了原理


- 原因:
	1. coding 域名证书有效期为三个月  

在第一次申请时 我阿里云解析路径 境外没有解析 所以是正常的 dns也没有 境外缓存 直接访问我的网站就是现实的内容

但是经过一段时间 dns会缓存 

[!](http://img.0x96m.com/hexo/ali_config.jpg)

[!](http://img.0x96m.com/hexo/coding_ok.jpg)
