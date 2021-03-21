---
title: "Data_Struct_MergeSort"
date: 2021-03-21T22:13:32+08:00
draft: true
---


```
归并排序：
将数据切割成多段进行排序
然后再多段合并

好处:
内存不够时，可以节约内存


func MergeSort(arr []int) []int {
	length:=len(arr)
	if length<=1 {
		return arr
	}
	n:=length/2
	frontArr :=MergeSort(arr[:n])
	rearArr :=MergeSort(arr[n:])

	return merge(frontArr,rearArr)
}

func merge(leftArr,rightArr []int)[]int  {
	leftIndex:=0
	rightIndex :=0
	res:=[]int{}
	for leftIndex<len(leftArr)&&rightIndex<len(rightArr){
		if leftArr[leftIndex] >rightArr[rightIndex] {
			res=append(res,leftArr[leftIndex])
			leftIndex ++
		}else if leftArr[leftIndex] < rightArr[rightIndex] {
			res = append(res,rightArr[rightIndex])
			rightIndex++
		}else {
			res =append(res,leftArr[leftIndex],rightArr[rightIndex])
			leftIndex++
			rightIndex++
		}
	}

	for len(leftArr)>leftIndex {
		res =append(res,leftArr[leftIndex])
		leftIndex++
	}
	for len(rightArr)>rightIndex {
		res =append(res,rightArr[rightIndex])
		rightIndex++
	}
	return res
}


```



