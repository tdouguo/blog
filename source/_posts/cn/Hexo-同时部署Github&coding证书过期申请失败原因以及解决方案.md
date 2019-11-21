---
title: Hexo-同时部署Github&coding证书过期申请失败原因以及解决方案
iscopyright: true
comments: true
lang: cn
abbrlink: 4195271328
date: 2019-11-11 18:32:26
updated: 2019-11-11 18:32:26
author:
tags:
	- SSL
	- 域名证书
	- Coding
	- Github
categories:
	- Hexo
---


# 前沿（吹牛逼）
每天码搬砖中~~

突然有一天想去看看自己网站 欣赏一下自己作品 

打开 咦这是为啥 显示证书不可用了

因我网站部署在github和coding上

我是国内访问所以去coding 看了一下 好吧~~ 过期了 coding域名证书为3个月~~（内心飘过1万个 ***）

# 问题以及解决方案

找到问题后 点击重新申请 显示的以下截图
[!](http://img.t-dou.net/hexo/coding_err.jpg)
仔细检查后发现还不行 google 一番后+(邮件联系coding技术支持)发现了原理

因第一次部署 dns还未存在缓存 所以coding默认认为他那里唯一解析直接同意证书申请了

但第二次因阿里云 境外解析为github  默认解析为coding


所以他获取证书时候不知道哪个是主哪个为辅 所以需要临时把境外解析暂停解析 
[!](http://img.t-dou.net/hexo/ali_config.jpg)

百度大概需要5分钟(实测 2 3s把 ) 暂停后重新申请即可~~

[!](http://img.t-dou.net/hexo/coding_ok.jpg)


---
华丽的分割线
---

继续装逼中~~~