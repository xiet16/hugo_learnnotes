---
title: "Data_Struct_Link"
date: 2021-03-21T01:16:40+08:00
draft: true
---

```
链表
地址不连续
删除插入O(1)
查找修改O(n)

顺序表：
查找修改 O(1)
内存连续
删除、插入O(n)
计算机理论上不存在大片连续的内存


为什么使用链表：
方便内存扩展，以及使用计算机内存碎片

节点的定义：数据+指向下一个数据的指针
type Node struct {
	data interface{}
	pNext *Node //存储下一个节点的地址
}

假设有一组数据： a d f h e
栈的特点：先进后出
实现: 头部插入，头部取出
type Node struct {
	data interface{}
	pNext *Node //存储下一个节点的地址
}

第一步：压入a
第二步：压入d, 这时数据的内存大致可以理解  d a
第三步：压入f,  这时数据的内存大致可以理解 f d a
同理：最后是  e h f d a
取得时候 从e 往下去


队列的特点 ： 先进先出
实现：尾部插入，头部取出，也可以反着来
type LinkQueue struct {
	front *Node //头部节点
	rear *Node //尾部节点
}
第一步：压入a ， front , rear 都指向a
第二步：压入d, 这时数据的内存大致可以理解  d a  , front 指向a, rear 都指向d
第三步：压入f,  这时数据的内存大致可以理解 f d a,  front 指向a, rear 都指向f
同理：最后是  e h f d a,  front 指向a, rear 都指向e
取的时候，操作front, 

操作上的区别，队列是两个node, 主要它用来记录首尾的节点

```




