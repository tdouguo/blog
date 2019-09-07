---
title: Docker+Wordpress建站问题总结记录
lang: cn
date: 2019-08-11 16:32:08
tags:
    - docker
    - wordpress
    - 解决方案
categories:
    - docker
---


## Wordpress] 仪表盘 - 设置更改固定连接后无法访问了 (更改未进行备案域名/未进行Nginx反向代理)
- 问题产生原因: 如果更改为域名(例如未进行备案域名) 因域名无法直接访问, 模拟请求过程
    1. PC电脑浏览器输入 IP:端口  
    2. Wordpress 收到请求后自动重定向设置的域名, 这时候域名无解析/未备案导致无法访问所以界面显示 404 或其他界面.
- 解决方案
    1. 登录云服务器
    2. 进入Docker-MySql
        ```
        查看正在运行的 docker进程
            $ docker ps 
        进入docker镜像内部
            $ docker exec -it fId bash
            如果启动镜像时指定name 则可以以name方式进入
            $ docker exec -it wp(启动时候的名称) bash 进入docker
        ```
        > fId 为运行时第一个 12位字母数字混合组合
        > 当看到 /$ 代表以及在此项docker中, exit退出
    3. 登入MySql, 进入数据库, 执行更新命令
        1. 登录
            ``` shell
            $ mysql -uroot -p 
            ```
        2. 回车并输入密码(密码无显示的) 启动mysql时的密码 
            > 如启动用户名不一样则 mysql -u用户名 -p 
            > 显示 mysql > 则代表以进入
        3. 进入数据库(要选择操控那个库)
            ``` shell
            $ show databales;    查看所有的库
            $ use wordpress;     进入 wordpress 
            ```
            > 显示 Database changed 代表切换成功
        4. 进入库后(必须切换要操作的库), 执行命令
            ``` shell
            查看所有的表  wp_options 中
                $ show tables;   
            查看表中数据当前是什么
                $ select * from wp_option where option_id=1;
            如忘记设置什么 这样查看 一般都是第一个option_value中域名 
                $ select * from wp_otion where option_value=‘从仪表盘设置的域名/IP’;
                $ select * from wp_otion where option_value link ‘%xx%’;   模糊查询 %是匹配所有前面有东西的
            更新命令  UPDATE 表名称 SET 字段=值  where 约束更改那些
                $ UPDATE wp_options SET option_value = replace( option_value, 'http://旧域名', 'http://新域名' ) WHERE option_name = 'home' OR option_name = 'siteurl';
                $ UPDATE wp_posts SET post_content = replace( post_content, 'http://旧域名', 'http://新域名' ) ;
                $ UPDATE wp_posts SET guid = replace( guid, 'http://旧域名', 'http://新域名' ) ;

                $ UPDATE wp_comments SET comment_content = replace(comment_content, 'http://旧域名', 'http://新域名') ;
                $ UPDATE wp_comments SET comment_author_url = replace(comment_author_url, 'http://旧域名', 'http://新域名') ;
            ```


---

## 运行后wordpress mysql链接失败 

- Q1 问题描述:

启动时IP使用127.0.0.1 / localhost / 0.0.0.0 管理界面初始化时访问失败
Docker-Wordpress连接 Docker-mysql


- A1 解决方案

创建一个 docker新网络 查看docker IP后重新启动

1. 添加一个 docker network 
    ```
    $ docker network create docker-mysql-net
    ```
2. 查看网络IP ifconfig 并记住 尝试使用新建的ip去连接



- 例如: 重新启动wordpress

``` docker
$ WORDPRESS_DB_HOST=172.18.0.1:3306 -e WORDPRESS_DB_USER=root -e WORDPRESS_DB_PASSWORD=123456-e WORDPRESS_DB_NAME=wordpress-p 8050:80 -d hub.c.163.com/library/wordpress  
注意其他配置都和之前运行一样 但是WORDPRESS_DB_HOST使用ifconfig查看的docker IP 启动
```


上述尝试之后还是无法解决排除问题

尝试 root 连接
    ```
        mysql -h0.0.0.0 -uroot -p密码
    ```

root可连接,但是自己新建的账号无法连接

- A2 解决方案
请对用户授权 %因权限不足,请授权, docker是归属一个单独的虚拟环境中网络Ip非127.0.0.1 localhost 所以需要授权%

1. root 连接进入
    ```
        mysql -h0.0.0.0 -uroot -p 密码
    ```
2. 授权
    ```
        grant all privileges on `数据库名称`.* to '用户名称'@'%' ;
    ```
