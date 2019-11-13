---
title: 博客搭建(Hexo+replica主题) 之 Url优化篇
iscopyright: true
comments: true
date: 2019-09-23 02:17:08
updated: 2019-09-23 02:17:08
abbrlink: hexo_seo_url
author:
lang: cn
tags:
    - hexo
    - seo
    - Hexo搭建博客优化
categories:
    - 搭建博客
---


- 文章URL优化策略（一）：自定义id属性

1.为每篇文章Front-matter添加id属性，作为文章URL，确保id属性的值满足以上条件。

2.编辑站点配置文件：
```
# permalink: :year/:month/:day/:title.html  # 默认永久链接冗长，title中存在中文字符。
permalink: :id.html # 尽量短，层次少，全小写，中划线连字，具有描述性，包含关键词
```

- 文章URL优化策略（二）：abbrlink链接唯一化

1.安装abbrlink插件：

```
$ npm install hexo-abbrlink --save  
```

2.编辑站点配置文件：
```
permalink: :abbrlink.html   # 生成唯一链接
abbrlink:
  alg: crc32  # 算法：crc16(default) and crc32
  rep: dec    # 进制：dec(default) and hex
```

标签&分类URL优化

我们在对文章分类或添加标签时，难免会用到中文或其他字符，而我们又在尽量避免中文字符出现在URL中，所以我们需要对中文分类&标签进行映射操作。


***参考链接***
- https://blog.csdn.net/yanzi1225627/article/details/77761488
