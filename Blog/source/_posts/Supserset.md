---
title: 可视化神器 Superset 
date: 2021-12-01 00:24:33
tags:
    - 学习笔记
    - 技术
    - 可视化神器 Superset
categories: 
    - 笔记
    - Superset
cover: https://i.loli.net/2021/11/30/tWp1uILjTMUczZh.jpg
---
 ### 快速部署(此部署方式需要外网,并且有很多依赖需要自己安装)
 > docker search superset  # 搜索公共镜像库可用superset容器


![1](https://i.loli.net/2021/11/30/ZnlPyeF2BaYJIvu.jpg)

> docker pull amancevice/superset #拉取镜像到本地

![2](https://i.loli.net/2021/11/30/B6LPxXkhEbHA23i.jpg)

> #后台运行容器并映射到8088端口,返回容器ID </br>
> docker run -p 8088:8088 -d amancevice/superset</br>
> #查看容器状态</br>
> docker ps</br>
> #进入容器并初始化superset,并注册用户</br>
> docker exec -it <容器ID> superset-init
 
![3.jpg](https://i.loli.net/2021/11/30/WEAYo5NQ1nDH6gU.jpg)</br></br>

接下来就可以通过 http://服务器IP:8088 访问superset啦</br>
- 重要说明

在安装过程中可能会报丢失依赖，根据报错信息，把依赖安装上去
在整个过程中，必须处在系统对应的python版本(我的是3.7)环境下执行命令</br></br>
参考官方文档 docker 介绍及安装:　https://docs.docker.com/engine/install/</br>
参考官方文档 superset 介绍：https://superset.apache.org/docs/intro 