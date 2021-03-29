---
title: "Nosql_Redis"
date: 2021-03-29T16:09:32+08:00
draft: true
---


```
1、redis 常用数据类型
string 
list
hash
set
zset 


2、redis 有效期
(1)redis 有效期的处理实际是对键的处理，Expires 保存了所有键的过期时间
(2)以下是四种过期策略（无过期值为-1）
EXPIRE 将key 的生存时间为ttl 秒
PEXPIRE 将key 的生存时间设为ttl 毫秒
EXPIREAT 以时间戳的方式设置生存时间为timestamp秒
PEXPIREAT 毫秒的时间搓
(3)例子
set key1 'value1'
exipre key1 20
expireat key1 1545470885
persist key1   //取消有效期，也就是设置其有效期为-1

(4) 清除失效数据机制
定时删除：在设置键的过期时间的时候创建一个定时器，当过期时间到的时候立马执行删除操作。不过这种处理方式是即时的，不管这个时间内有多少过期键，不管服务器现在的运行状况，都会立马执行

惰性删除：惰性删除策略不会在键过期的时候立马删除，而是当外部指令获取这个键的时候才会主动删除。处理过程为：接收get执行、判断是否过期（这里按过期判断）、执行删除操作、返回nil（空）

定期删除：定期删除是设置一个时间间隔，每个时间段都会检测是否有过期键，如果有执行删除操作

(5) redis 内存满了
设置内存大小
config set maxmemory 100MB /config get maxmemery
内存淘汰机制：
noeviction(默认)：不再提供写请求，返回错误
allkeys-lru : 在所有的key 中使用lru 算法对数据进行淘汰
volatile-lru: 在设置了"过期时间"的key 中使用lru 算法进行淘汰
allkeys-random : 在所有key 中随机淘汰
volatitle-random: 在设置了“过期时间”的key中设置了淘汰
volatitle-ttl: 看着就知道了，最早过期的最新淘汰

3、redis 持久化
[ridis 持久化](http://example.net/)

4、redis主从复制

(1)redis的主从同步分为两种，分为全量同步和增量同步。
只有从机第一次连接上主机是全量同步。
断线重连很有可能触发全量同步也有可能是增量同步（master判断runid`是否一致）

全量同步主要分为三个阶段：
同步快照阶段：Master创建并发送快照给Slave，Slave再入快照并解析。Master同时将此阶段产生的新的命令写入到积压缓冲区中。
同步写缓冲阶段：Master向Slave同步存储在缓冲区的写操作命令。
同步增量阶段：Master向SLave同步写操作命令。

Redis增量同步主要是指Slave完成初始化开始正常工作时，Master发生的写操作同步到Slave的过程。
通常情况下，Master没执行一个写命令就会想Slave发送相同的写命令，然后Slave接受并执行

简书上的说明，我觉得可以
[redis 主从复制](https://www.jianshu.com/p/40212051ccc9)


```




