---
title: 博客搭建(Hexo+replica主题) 之 部署篇
iscopyright: true
comments: true
lang: cn
tags:
  - hexo
  - github
categories:
  - 博客搭建(Hexo+replica主题)
abbrlink: 844841121
date: 2019-08-11 16:27:45
---


## 环境需求

- [Nodejs(8.0.2+)](https://nodejs.org/en/)
    - [hexo](https://hexo.io/zh-cn/docs/)
- [Git(2.13.1+)](https://nodejs.org/en/)

## 快速开始

- clone 文档项目

```shell
$ git clone https://github.com/CnTDou/tdou.cc.git tdou_cc
```

- 安装项目依赖包

```shell

$ cd tdou_cc && npm install && npm install -g hexo-cli

```

- 因当前项目主题是基于子模块引用更新子模块

```shell
$ git submodule update --init --recursive
```

- 启动开发者服务器

```shell
$ hexo s
```

如果您打开浏览器并访问`http://localhost:4000`,您应该看到文档网站已启动并正在运行。


- 分支说明
    - ***maseter***  hexo自动部署&github-pages
    - ***v1.0*** 当前项目源文件


- 其他命令 

```
hexo init                # 初始化，安装所需包
npm install              # 其实此句不是必须，新版本的Hexo在初始化时就安装好了依赖包)

hexo n          # 新建文章，在\source\_posts文件夹里
hexo new page   # 新建页面，比如想在导航栏新增一个“关于我”的页面
hexo clean      # 清除本地的数据库和生成的public文件夹
hexo g          # 生成博客文件
hexo s          # 运行在本地浏览器，可当预览使用
hexo d          # 部署博客到Github等
```


### 其他

- 功能:
    - [gulp压缩优化]()
    - [travis自动部署]()
    - [Disqus评论]()
    - [google&百度收录]()
        - [百度资源搜索平台](https://ziyuan.baidu.com)
        - [google search console](https://search.google.com/)
    - [Google Analytics and 百度统计]()
        - [百度统计](https://tongji.baidu.com)
        - [Google Analytics](https://analytics.withgoogle.com)


- FAQ
    - Q: not code-js
        ```
        $ npm install core-js@2
        ```
    - Q: hexo d 无响应了
        > 检查 _config.yml git 配置是否 ssh

- 接入评论
    - https://www.jianshu.com/p/57afa4844aaa
    - https://sjq597.github.io/2018/05/18/Hexo-%E4%BD%BF%E7%94%A8Gitment%E8%AF%84%E8%AE%BA%E5%8A%9F%E8%83%BD/
    
    
- 参考
    - https://hexo.io/zh-cn/docs/deployment
    - https://www.jianshu.com/p/2b09156ee5b1
    - [Gitment评论功能接入](https://www.jianshu.com/p/57afa4844aaa)
    - https://blog.csdn.net/u012040909/article/details/79929542
    - https://blog.csdn.net/nqmysbd/article/details/88764425
    - [hexo d -g 踩坑记](https://www.jianshu.com/p/9a137d8e554a)
