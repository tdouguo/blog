---
title: 利用travis自动部署hexo搭建在github的博客
date: 2019-08-03 01:36:48
tags:
    - 建站记录
    - hexo
    - hexo部署
categories:
    - 建站记录
---


--- 

- Q1:安装travis中报错

``` bash
$ gem install travis

ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /Library/Ruby/Gems/2.3.0 directory.

```

- A1: 权限不足

``` bash
$ sudo gem install travis
或
$ sudo gem install -n /usr/local/bin travis 
```

---

- Q2: travis 未授权
``` bash
$ travis login --auto

(you github name) has not granted Travis CI the required permissions, please log in via travis-ci.org
```

- A2: 去 travis 授权 
    1. 登录官网  https://www.travis-ci.com/
    2. github 登录自动关联
    3. 重试即可成功

- A3: 打开后始终 404 没有样式 ,怀疑主题问题 在 travis 中 主题并没有pull,我定制化更改主题一些内容还无法使用源主题,所以我基于git 子模块方式去实现
    1. fork 源项目
    2. 新建一个分支 更改并push
    3. 在本机 git submodule init
    4. git submodule add https://github.com/Kylin-Studio/hexo-theme-replica.git /theme/replica
        - 注意 此处使用 https 形式 并且主题是开放开源的, 如私有自查解决方案
    5. git add .gitmodules
    6. git commit -m "add submodules"
    7. git push  自动打包成功

- A4: travis 部署gulp 无法压缩

---


## 优化 使用gulp 压缩
- [gulp 4的坑](https://blog.csdn.net/edc3001/article/details/86078572)



- 参考: 
    - https://blog.csdn.net/qq_23079443/article/details/79015225
    - https://blog.i1hao.com/2018/09/01/hexo-and-githubpages-best-practices/
    - [手把手教你使用Travis CI自动部署你的Hexo博客到Github上](https://blog.csdn.net/woblog/article/details/51319364)
    - [通过Travis来自动构建博客](https://www.jianshu.com/p/38ee582bd0ea)
    - [手把手教从零开始在GitHub上使用Hexo搭建博客教程(四)-使用Travis自动部署Hexo(1)](https://www.jianshu.com/p/7f05b452fd3a)
    - [手把手教从零开始在GitHub上使用Hexo搭建博客教程(四)-使用Travis自动部署Hexo(2)](https://www.jianshu.com/p/fff7b3384f46)
    - [travis自动部署排坑日记](https://www.jianshu.com/p/630d75e4697e)
    - [Travis-ci 远程构建 + 自动化部署](https://hacpai.com/article/1534086971693)
    - [用 Travis CI 自動部署網站到 GitHub](https://zespia.tw/blog/2015/01/21/continuous-deployment-to-github-with-travis/)
    - [使用travis-ci自动部署github上的项目](https://www.cnblogs.com/morang/p/7228488.html)
    - [利用travis自动部署hexo搭建在github的博客](https://sabrinaluo.github.io/tech/2015/12/28/travis-github-hexo/)

- 其他部署方式:
    - [利用travis进行heroku部署](https://sabrinaluo.github.io/tech/2016/06/02/travis-heroku/)
    - [用webpack打包react组件](https://sabrinaluo.github.io/tech/2017/08/14/react-component-with-webpack/)
