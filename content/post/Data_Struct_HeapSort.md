---
title: "Data_Struct_HeapSort"
date: 2021-03-21T17:15:34+08:00
draft: true
---

```
堆排序

原理:
堆排序就是二叉树排序 假设5>3, 3>1 , 则 5>1
循环次数

假设把数组看成如下树形结构
						          N1(a[n])
						
			  N2(a[2*n+1])                               N3(a[2*n +2]) 
N4(a[2*n+1])               N5(a[2*n +2])    N6(a[2*n+1])               N7(a[2*n +2]) 

深度: length/2 +1

第一步:N2，N4,N5 做三节点排序，把最小的值赋给N2节点
第二步:N3,N6,N7 做三节点排序，把最小值赋给N3
第三步:同理，N1,N2,N3 做三节点排序，把最小值赋给N1，这时候，数组的第1个就是最小值
第四步：数组第1位和最后一位做调换，长度减1，当做新数组，进入下一次循环（重复第一第二第三步骤）


关键代码
deap :=length/2+1  //计算深度
for i:=deap-1;i>=0;i-- {
	maxValue := i
	leftChildren:=2*i +1  //左孩子节点
	rightChildren :=2*i+2  //右孩子节点
	//防止数组溢出
	if leftChildren <= length-1 && arr[leftChildren]<arr[maxValue]{
		//arr[leftChildren],arr[maxValue]=arr[maxValue],arr[leftChildren]
		//这样写也行
		maxValue = leftChildren
	}

	if rightChildren <=length-1 && arr[rightChildren]<arr[maxValue] {
		//arr[rightChildren],arr[maxValue]=arr[maxValue],arr[rightChildren]
		maxValue =rightChildren //
	}

	if maxValue!=i {
		arr[maxValue],arr[i]=arr[i],arr[maxValue]
	}
}


```




