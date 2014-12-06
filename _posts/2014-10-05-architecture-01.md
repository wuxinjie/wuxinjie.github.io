---
layout: post
title: 架构：.NET高并发架构方案 
catgroy: designPattern
---


###缓存系统：
* 1级是网络级缓存，缓存在浏览器、CDN以及代理服务器中。
* 2级由.Net框架 HttpRuntime.Cache完成，在每台服务器的内存中。
* 3级Redis或者Memcache，分布式内存键值存储，在多个支撑同一个站点的服务器上共享缓存项。
* 4级SQL Server Cache，整个数据库，所有数据都被放到内存中。
* 5级SSD。通常只在SQL Server预热后才生效

###负载均衡：
* 方式：DNS负载均衡、IP负载均衡、反向代理负载均衡
* 硬件：F5
* 软件：Haproxy、 Nginx、 LVS或者IIS自带的ARR
* 算法：循环法、加权循环法、最少连接、基于负载

###多服务器session共享：
* 方式：stateServer 或者保存到数据库
* 高可用性：多台状态服务器
* 类别：同步、异步

###资源服务器共享：
* 单独的服务器用来存储跟读取共享文件

###数据库：
* MSSQL 数据库集群或者分布式
