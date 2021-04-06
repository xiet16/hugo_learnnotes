---
title: "Go_iota"
date: 2021-04-06T18:48:06+08:00
draft: true
---


```
iota 是go语言常量计数器，只能在常量表达式中使用

每出现一次const , iota 就会被重置为0， const 中每新增一行，iota 就计数一次，相当于const 的行索引

func IotaTest()  {
   fmt.Println(Bt,"-->",Kb,"-->",Mb,"-->",Km,"-->",Zm,"-->",a)
}

func IotaTest()  {
   fmt.Println(Bt,"-->",Kb,"-->",Mb,"-->",Km,"-->",Zm,"-->",a,"-->",Em,"-->",Hm)
}

const a = iota

const (
	Bt = 8
	Kb = 8<<iota
	Mb
	Km =iota
	Zm = 100
	Em
	Hm
)

8 --> 16 --> 32 --> 3 --> 4 --> 0 --> 100 --> 100

Em和Hm 为什么是100 ，就和Mb 为什么是 8<<iota 一样，const 在编译 是，取的是上一个表达式来解析


const ( 
	_  = iota  //0
 	KB = 1<<(10*iota) //1<<10*1  
	MB                //1<<10*2
	GB
)


常量的值必须在编译期间确定。因此不能将函数的返回值赋给常量，因为函数调用发生在运行期

```







