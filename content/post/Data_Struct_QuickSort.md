---
title: "Data_Struct_QuickSort"
date: 2021-03-21T18:27:13+08:00
draft: true
---


```

快速排序:
特点:
取基数，以基数为基准，将数组分为大于基数，等于基数，小于基数三个数组
递归再进行快速排序

关键代码
base:=arr[0]
low:=[]int{}
high:=[]int{}
mid:=[]int{}

mid=append(mid,base)
for i:=1;i<length;i++ {
	if base>arr[i] {
	  low=append(low,arr[i])
	}else if base <arr[i] {
		high=append(high,arr[i])
	}else {
		mid=append(mid,arr[i])
	}
}
low,high = QuickSort(low),QuickSort(high)
res:=append(append(high,mid...),low...)


```





