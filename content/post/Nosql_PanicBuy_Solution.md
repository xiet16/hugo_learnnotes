---
title: "Nosql_PanicBuy_Solution"
date: 2021-03-30T08:58:48+08:00
draft: true
---


```
秒杀系统分析
限流：
消峰：由于有瞬间有大量用户涌入
异步处理：
内存缓存：数据库读写有瓶颈，因为它的读写是基于磁盘IO

单机版的redis qps 大概在8w 左右
集群版访问原理：假设有三个Node1、Node2、Node3 ，
第一次访问A商品数据时，通过hash ，找到A商品所在的Node ,然后返回
所以，集群只是分担了总的Qps , 而不是提高了Qps,单个商品的Qps 并没有提升

在12核cup 的条件下，单个接口能承受20-30w 

通过go 的并发机制+redis  可以实现商品高并发下的秒杀。但是无法解决数据库订单量的生成以及商品数的修改。这个时候就要用到消息队里

流量控制：
消息队列：避免瞬间的流量给数据库带来巨大的压力，

使用模式autoack :true +qos   手动应答的方式,每次只消费一个订单
Qos{
 prefetchcount :1,  每次只消费一个
 prefetchSize :0 ,    服务器传递的最大容量，8个字节
 global :false,   //只对当前消费队列    ，如果true  对所有channel 可用
}

redis 分布式锁：setnx + 续命锁（redisson 用的是hset +续命锁）
redis 主从锁失效问题：只有半数以上的锁加成功以后，才返回加锁成功
如何提高分布式锁性能：分段锁
缓存数据库双写不一致：缓存双删（问题没法解决）、分布式锁

```



