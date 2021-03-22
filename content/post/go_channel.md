---
title: "Go_channel"
date: 2021-03-22T19:42:00+08:00
draft: true
---


```
感慨一下：一直想总结一下这个来着，但总有些心虚，说到底，一是没有仔仔细细证明过底层的代码。二是，感觉channel 这东西，说简单，也 简单，说不简单吧。总想着，自己是不是还有没遇到的坑。不过还是先总结一下吧

channel：

特点：
1、同一时间点，只能被一个协程访问,也就是说它是同步的 、线程安全的，
2、管道分为有缓冲和无缓冲
3、无缓冲情况下：在接收者准备好之前，发送者是阻塞的也就是说，首先得有接收者开始接收，才会开始发送
4、有缓冲情况下：在buf 满之后，直到有接收者接收，发送者才可以发送

type hchan struct {
	qcount   uint           // total data in the queue
	dataqsiz uint           // size of the circular queue
	buf      unsafe.Pointer // points to an array of dataqsiz elements
	elemsize uint16
	closed   uint32
	elemtype *_type // element type
	sendx    uint   // send index
	recvx    uint   // receive index
	recvq    waitq  // list of recv waiters
	sendq    waitq  // list of send waiters

	// lock protects all fields in hchan, as well as several
	// fields in sudogs blocked on this channel.
	//
	// Do not change another G's status while holding this lock
	// (in particular, do not ready a G), as this can deadlock
	// with stack shrinking.
	lock mutex
}

channel 的线程安全，是基于lock 机制的
buf 是一个环形队列，初始化时sendx 、recvx 都为0

```




