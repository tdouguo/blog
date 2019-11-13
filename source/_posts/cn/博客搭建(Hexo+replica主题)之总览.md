---
title: Hexo博客 | github page&coding部署、hexo、travis-co、seo、评论、搜索、统计、广告、Url优化
lang: cn
tags:
  - hexo
  - hexo-replica
  - travis-ci
  - seo
  - disqus
  - 评论
  - google-search
  - 百度统计
  - Google-Analytics
  - FlagCounter
  - Google-AdScene
categories:
  - 博客搭建HexoAndreplica主题)
abbrlink: hexo
---

持续更新中 . . .


# 功能列表

- [x] 基于 [Hexo](https://hexo.io/) + [Hexo 主题 replica](https://github.com/sabrinaluo/hexo-theme-replica)实现站点以及md文章编写
- [x] 基于 [github page](https://github.com) 和 [coding](https://coding.net) 实现代码托管和部署
- [x] [自动化部署] 基于[travis-ci](https://travis-ci.com) 自动化部署 push github:master代码后即可自动部署  github:gh-page & coding
- [x] [SEO] 使用GULP 进行代码压缩
- [x] [SEO] 站点地图 百度=html、google=xml 
- [x] [SEO] robots.txt 站点机器人爬取规则 更快收录 [自动生成web工具](http://tool.chinaz.com/robots/)
- [x] [SEO] 基于七牛图床实现图片存储,基于[PicGo](https://molunerfinn.com/PicGo/)实现图片管理 需要已经备案的域名
- [x] [评论] [disqus](https://disqus.com/)
- [x] [Google搜索](https://search.google.com/)
- [x] [统计] [百度统计](https://tongji.baidu.com/)、[Google Analytics](https://google.com/analytics/)、[访客统计FlagCounter](http://www.flagcounter.com/) [教程](https://blog.csdn.net/kl28978113/article/details/79500217)
- [x] [站点广告] [google adscene](https://www.google.com/adsense/)
- [x] [SEO] 文章URL优化

- [ ] [SEO] 关键字优化,外链


## 目录

- SEO - [Hexo搭建博客之Url优化](https://tdou.cc/cn/hexo_seo_url.html)
- [Hexo搭建博客之站点配置文件详解](https://tdou.cc_cn/hexo_config.html)


# 菜鸟式搭建教程

- v0.0.1 目标: 实现 Hexo主题+GitHub部署
- v0.0.2 目标: 实现 Travis-ci 持续集成
- v0.0.3 目标: 实现 Coding同步Github部署
- v0.0.4 目标: 实现 域名绑定Github 以及 CHAME同时解析CODING

- SEO 优化
    - v0.0.x.配置 目标: 实现 GULP 压缩以及Travis-ci 的自动部署
    - v0.0.x.配置 目标: 站点地图配置
    - v0.0.x.配置 目标: robots.txt   

- 其他自定义配置
    - v0.0.x.配置[建议] 统计配置
    - v0.0.x.配置[非必须] 评论配置
    - v0.0.x.配置[自行决定] SEO 七牛图床


## 其他链接
- 敬请期待: [如何使用Git以及在Github创建一个代码仓库](https://tdou.cc/)


---

## 附加其他
- 主题:(social)链接 左侧个人信息无法添加其他的图标+链接对应解决方案
    - Q1-更改左侧intro信息链接脚本路径 */themes/replica/layout/intro.ejs
        - Q: 因主题icon基于 http://www.fontawesome.com.cn/faicons/ 获取的图标，部分图片开源库中没有,导致无法引用链接,例:csdn、博客园、知乎、简书
        - A: 找到替换方案 https://www.iconfont.cn/, 使用方式:https://www.jianshu.com/p/5d4a39cdf96d
    - Q2-更改页脚菜单中链接脚本路径 */themes/replica/layout/_partial/footer.ejs

- 博客站点 [http://tdou.cc](http://tdou.cc/)

github源代码开源地址 : [https://github.com/t-dou/tdou.cc](https://github.com/t-dou/tdou.cc)

> master分支为存放 hexo源项目+md博文
> gh-pages 分支存放为 travis-ci 自动生成的html文件

主项目的主题以子模块方式引用 地址: https://github.com/T-Dou/hexo-theme-replica
 