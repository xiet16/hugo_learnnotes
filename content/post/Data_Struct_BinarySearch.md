---
title: "Data_Struct_BinarySearch"
date: 2021-03-24T11:23:01+08:00
draft: true
---


```
二分查找：
从中间查找，前提是排了序的数据


关键代码：

func BinarySearch(arr[] int ,data int) int {
     left:=0
     right:=len(arr)-1
	for left <right{
		mid := (left+right)/2
		if arr[mid]>data {
			left =mid+1
		}else if arr[mid]<data{
			right=mid-1
		}else {
		    return mid
		}
	}
	return -1
}

```



