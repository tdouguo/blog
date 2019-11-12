# 基于Hexo+replica主题做的个人博客


## [总览](https://tdou.cc/cn/hexo_jianzhan.html)
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


## [站点日志](https://tdou.cc/changelog.html)

- 2019.11.12
	- [百度收录](https://blog.csdn.net/qq_32454537/article/details/79482914) 因域名无法备案 百度不收录 百度某一时间点做百度快照

- 2019.09.06
    - google adscene 正式使用
    - 基于picgo 七牛图床实现图片管理 [参考](https://github.com/Molunerfinn/PicGo/releases)

- 2019.08.19
    - 添加搜索生成插件 [参考](https://www.itfanr.cc/2017/10/27/add-search-function-to-hexo-blog/)
    - 整理项目结构区分多语言版本
    - 添加 [google-adscene](https://www.google.com/adsense) (未测试)

- 2019.08.11
    - 百度统计 & Google Analytics
    - Google Custom Search Engine^1
    - [Disqus](https://www.jianshu.com/p/d68de067ea74?open_source=weibo_search) 

- 2019.08.08
    - travis 部署使用gulp压缩

- 2019.08.06
    1. 解决travis 部署相关问题
        - travis显示部署但访问404 [问题:无主题,子模块方式加入]

- 2019.08.03-2019.08.05
    1. 解决travis 部署相关问题
        - ssh无法部署成功,切换token方式
        - github 域名无法解析 [问题:CNAME]
        - 基于token实现 github coding同时部署

- 2019.08.03
    1. 基于replica v2.1.0 完成基础功能并接入
    2. 接入持续集成自动部署方案 travis



