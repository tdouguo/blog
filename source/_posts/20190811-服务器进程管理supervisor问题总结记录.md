---
title: 服务器进程管理supervisor问题总结记录
date: 2019-08-11 16:49:56
tags:
    - supervisor
    - command
    - 服务器
categories:
    - 解决方案
---


Q1: Supervisorctl error: unix:///var/run/supervisord.sock refused connection?

A1: 指定配置文件 supervisord -c /etc/supervisor/supervisord.conf
清理无用配置因配置错误导致无法启动