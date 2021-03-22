---
title: "Data_Struct_ShellSort"
date: 2021-03-22T08:45:08+08:00
draft: true
---

```

希尔排序：

特点:
是一种步长收缩算法，一般初次增量为序列的一半
本质上是一种分组
时间复杂度为O(n3/2)
可以用多线程

关键点：
如何定义步长


关键代码
gap :=length/2
for gap>0 {
	for i:=0;i<gap;i++ {
		ShellStep(arr,i,gap)
	}
	gap/=2
}


//间隔为步长的插入算法
length:=len(arr)
for i:=start+gap;i<length;i+=gap {
	//间隔为gap 的插入排序
	backup :=arr[i]
	j:=i-gap
	//数据循环往后移动
	for j>=0 && backup>arr[j]{
		arr[j+gap] = arr[j]
		j-=gap
	}
	arr[j+gap]=backup //插入
	fmt.Println(arr)
}



```
