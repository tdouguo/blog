---
title: ubuntu搭建svn
date: 2019-08-16 14:06:42
tags:
categories:
---

# 安装svn

- 配置教程: https://blog.csdn.net/zengsange/article/details/80618301
- 其他配置教程[开机启动] https://www.cnblogs.com/chen-lhx/p/5805716.html



- 启动服务器
    > svnserve -d -r /usr/svn/

- 查看运行状态
    > ps aux | grep svnserve

- 停止
    > killall svnserve


# 依赖nginx代理转向域名

- vi /etc/nginx/conf.d/svn_nginx.conf

``` nginx.config
	server {
		# 监听 80 端口
		listen 80;
		autoindex on;
		server_name svn.tdou.cc;
		access_log /var/log/nginx/svn_access.log;
		error_log /var/log/nginx/svn_error.log;
		index index.html index.htm index.jsp index.php;
		if ( $query_string ~* ".*[\;'\<\>].*" ){
			return 404;
		}
		location / {
			# 反向代理到 8080 端口
			proxy_pass http://127.0.0.1:3690;
			add_header Access-Control-Allow-Origin *;
		}
	} 
```

- 验证ngxin nginx -t 
- 重启nginx /etc/init.d/nginx restart 

- 验证OK 重启失败
	```
		[....] Starting nginx (via systemctl): nginx.serviceJob for nginx.service failed because the control process exited with error code.
		See "systemctl status nginx.service" and "journalctl -xe" for details.
		failed! 
	```
	- http://www.chenxm.cc/article/40.html
	- https://www.digitalocean.com/community/questions/can-t-start-nginx-job-for-nginx-service-failed

- 我这里同时启动 apache2 和nginx 因apache2无用我停止了