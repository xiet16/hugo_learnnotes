---
title: "Go_persistence"
date: 2021-04-09T08:36:43+08:00
draft: true
---

```
redis 持久化

rdb（redis database）
保存文件：dump.rdb
默认模式 15分钟1次 、5分钟 10次   1分钟1w 次
过程：Fork 一个线程执行，Fork 操作会复制主线程，包括其数据，并且作为其子线程
save bgsave : save 会阻塞进程 
优势：适合大数据的恢复，响应快
劣势：fork 可能会造成很大的资源消耗，最后一次持久化后的数据有可能丢失


aof(append only file)：以日志的形式记录每一个写操作，只许追加，不许改写
默认不开启
策略：同步操作（appendfsync），always、everysec 、no；默认是每秒一次
如果同时开启了rdb , 默认从aof 读取
rewrite 原理：fork 一个新进程，遍历进程中内存的数据，重新写一个aof 文件
rewrite 触发机制：记录上一次的aof 大小，默认是大于1倍且大于64MB
优势：数据完整性较好，有可能有1秒的数据丢失
劣势： AOF 运行效率要慢于rdb

```



