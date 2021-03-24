---
title: "Data_Struct_QuickSortPlus"
date: 2021-03-24T10:16:01+08:00
draft: true
---


```
快速排序升级算法：
前面的快速排序有个弊端，就是频繁的开辟数组，造成内存不断的飙升，而且数据超过2000w时，排序的时间大大增加

原理:
取基数，小于基数的往左边插入，大于基数的往右边插入，等于的记录等于的起始位置
所以会有几个下标，[0-lt] 是小于 基数的下标，[lt-i]是等于基数的下标，[i-gt]是移动下标，当i==gt 时，此时[gt-length]是大于基数的下标

/*
3,2,8,6,9 1,5
取基数，这里每次都取arr[0]
小于的从第0位开始交换
大于的从最后一位开始放尽管扔到一变就好了
3,2,8,6,9,1,5  第一次循环，vdata=arr[0]=3 ,不动
3,2,5,6,9,1,8  第二次循环 3<a[2]=8   gt-1
3,2,1,6,9,5,8   第三次循环 3<a[2]=5 gt -1
3,2,1,6,9,5,8   第四次循环 3>a[2]=1 这时候是不变的
3,2,1,9,6,5,8   第六次循环 3《a[3]=6 这时候是不变的 gt-1
3,2,1,9,6,5,8   第七次循环 3《a[3]=9 这时候是不变的 gt-1 ， 这个时候i==gt
1,2,3,9,6,5,8   第八次循环
*/

关键代码:

func QuickInsertSort(arr []int,left int,right int) []int {
	//数组只剩3个时，用插入排序
	if right-left <3 {
		InsertQuick(arr,left,right)
	}else {
		//随机找一个数字
		Swap(arr,left,rand.Int()%(right-left+1)+left)
		vdata :=arr[left] //基数
		lt :=left //arr[left+1,lt] <vdata
		gt:=right+1  //arr[gt... r] >vdata
		i:=left+1    //arr[lt+1 ...i] ==vdata
		for i<gt {
			if arr[i]<vdata {
				Swap(arr,i,lt+1) //这个是不是有点多此一举，
				lt++
				i++
			}else if arr[i]>vdata {
               Swap(arr,i,gt-1)
               gt--
			}else {
				i++
			}
		}
        Swap(arr,left,lt) //交换头部位置
        QuickInsertSort(arr,left,lt-1)
		QuickInsertSort(arr,gt,right)
	}
	return arr
}

//升序插入算法
func InsertQuick(arr []int,left,right int){
	for i:=left;i<=right;i++ {
		temp := arr[i]
		var j int
		for j=i;j>left&&arr[j-1]>temp;j-- {
			arr[j] = arr[j-1]  //循环
 		}
		arr[j]=temp //插入
	}
}

//数据交换
func Swap(arr []int,i,j int)  {
    arr[i],arr[j] =  arr[j],arr[i]
}


```





