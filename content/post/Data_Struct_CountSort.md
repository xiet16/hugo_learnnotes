---
title: "Data_Struct_CountSort"
date: 2021-03-22T12:05:28+08:00
draft: true
---


```
统计计数算法：
不基于元素比较的排序算法

举个简单的例子讲吧：
假设有一组数据： 4，3，6,  9，7 ，8
(1)取其中最大值9，这里通过一轮比较就可以得出
(2)建一个长度为9+1=10的数组countarr，用数组的下标代表数据，
    也就是arr[9] 中的[9]代表9 ,arr[9] 代表出现多少次
(3) 统计次数后的countarr:   [0 0 0 1 1 0 1 1 1 1]
(4) 其实这个时候已经排好序了，只要用下标和个数循环输出就行
(5) 有时候我们想知道，数组中的任意某个值是第几位，这时候进一步衍生下面的步骤
     循环往后叠加，countarr[i]+=countarr[i-1],这里需要理解，比如[0 0 0 1 1 变为
     [0 0 0 1 2   这里的1变为2，代表的是[4] 排在第二位，以此类推完整的是这样
     [0 0 0 1 2 2 3 4 5 6]   最后一位6很容易看出来，一共有6个数据，下标[9] 在第六位


关键代码：

maxValue := GetMaxValue(arr)
	countArr:=make([]int,maxValue+1)
	res:=make([]int,length)

	for i:=0;i<length;i++ {
		countArr[arr[i]]++  //统计次数
	}
	fmt.Println("统计次数:",countArr)

	for i:=1;i<=maxValue;i++ {
		countArr[i]+=countArr[i-1] //叠加
	}
	fmt.Println("次数叠加:",countArr )

    //展开数据
	for _,v:=range arr{
		res[countArr[v]-1] =v
		countArr[v]--
	}

	return res


```




