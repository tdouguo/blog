---
title: Docker+Wordpress建站教程
iscopyright: true
comments: true
lang: cn
tags:
  - docker
  - wordpress
categories:
  - 建站教程
abbrlink: docker_wordpress
date: 2019-08-11 16:17:46
---


- 运行环境
    - Docker
    - Docker-Mysql
    - Docker-Wordpress
    - Ubuntu 18.04

## Docker 常用名称
- 详情查看Docker 常用命令一篇


## Docker-Mysql
- 参数汇总
    - MYSQL_ROOT_PASSWORD：设置 mysql 数据库的密码。
    - MYSQL_DATABASE：设置 mysql 的数据库名称。
    - MYSQL_USER：设置 mysql 的数据库用户。

## Docker-Wordpress 
- 参数汇总
    - WORDPRESS_DB_HOST：wordpress 连接数据库的参数默认 ip：port 
        > ! 注意 此项IP 使用 ifconfig 查看 docker0 ip多少
    - WORDPRESS_DB_USER：wordpress 连接数据库的用户 
    - WORDPRESS_DB_PASSWORD：wordpress 连接数据库的密码
    - WORDPRESS_DB_NAME：wordpress 数据库的名称默认为：wordpress

- 安装命令
    > docker pull hub.c.163.com/library/wordpress:latest
    > docker pull hub.c.163.com/library/mysql:latest

- 启动命令
    ```
    docker run -p 3306:3306 -e MYSQL_ROOT_PASSWORD=000000 -e MYSQL_DATABASE=wordpress -d hub.c.163.com/library/mysql
 
    docker run --name wp -p 8050:80 -e WORDPRESS_DB_HOST=服务器内外IP:3306 -e WORDPRESS_DB_USER=root -e WORDPRESS_DB_PASSWORD=123456 -e WORDPRESS_DB_NAME=wordpress -d wordpress

    注意 此处的WORDPRESS_DB_HOST地址为 服务器的内外地址 不可写 127.0.0.1 0.0.0.0 localhost  因为这地址是代表在docker内部的 运行一个镜像 内部所有的环境都是独立的 可以看成一个服务器 运行docker镜像后 这个docker镜像的所有都是独立的  
    ```

- 更新域名
    - 查看 [Docker-Wordpress建站问题总结记录](https://tdou.cc/)@{docker域名/IP更新}


### 参考
- https://blog.51cto.com/14314637/2406710?source=dra
- https://blog.csdn.net/xiaoping0915/article/details/79515309
- https://blog.csdn.net/f59130/article/details/74014260
- [Ubuntu安装与卸载docker](https://blog.csdn.net/longzhoufeng/article/details/82421322)
1. gitbook@{一念成魔} - [Docker 入门之个人博客搭建教程](https://gitbook.cn/books/5b63feefd66d4772839a2418/index.html)
2. 菜鸟教程 - [Docker教程](https://www.runoob.com/docker/docker-tutorial.html)
3. https://blog.csdn.net/satomic/article/details/79117954 
4. https://www.linuxidc.com/inux/2017-07/145699.htm
