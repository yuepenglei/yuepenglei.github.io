---
title: 插入排序
date: 2018-11-28 22:02:00
categories: 算法 #分类
tags: [算法,插入排序,排序]
description: 插入排序是一种简单的插入排序法，其基本思想是：把待排序的记录按其关键码值的大小逐个插入到一个已经排好序的有序序列中，直到所有的记录插入完为止，得到一个新的有序序列。
---

# 插入排序
- **该篇文章为本人阅读《算法》一书所做笔记以及知识总结，以供未来查阅**

### 定义

> 插入排序是一种简单的插入排序法，其基本思想是：把待排序的记录按其关键码值的大小逐个插入到一个已经排好序的有序序列中，直到所有的记录插入完为止，得到一个新的有序序列。—— <a href="https://baike.baidu.com/item/%E6%8F%92%E5%85%A5%E6%8E%92%E5%BA%8F" target="_blank"> [ 百度百科 ]


### 解释说明

在插入排序中，每次确定一个元素的插入位置，在确定过程中，我们会将该元素依次与前一个元素作对比，如果前一个元素比该元素大，则交换二者的位置（假定我们按照从大到小排序），直至前一个元素比该元素小时，停止对比，这就意味着该元素找到了目前最合适的位置。

上面是排序的基本过程，假定我们有一个待排序的数组，长度为10。

首先我们取出第二个元素，将其与前一个元素对比，若第前一个元素大于该元素，则交换位置，然后我们就为数组的前两个元素排序完成。

其次我们取出第三个元素，将其与前一个元素对比，若第前一个元素大于该元素，则交换位置，然后重复对比过程，直至前一个元素小于该元素，则我们就为数组的前三个元素排序完成。

以此类推，最终我们就能完成整个数据的排序。在这个过程中，我们会发现，待排序元素前面所有的元素都是有序的。

###### 代码块
```java
public class Test {	
	public static void main(String[] args) {
		String[] strArray = new String[]{"S", "O", "R", "T", "E", "X", "A", "M", "P", "L", "E"};
		sort(strArray);
	}
	//排序
	public static void sort(String[] strArray){
		System.out.println("排序前：" + print(strArray));
		//插入排序算法开始
		int length = strArray.length;		
		for(int i = 1; i < length; i++){
			//compareTo()方法是java类库的方法，A.compareTo(B)，如果A小于B则返回负数，A等于B则返回零，A大于B则返回整数
			for(int j = i; j > 0 && strArray[j].compareTo(strArray[j - 1]) < 0; j--){
				exch(strArray, j, j - 1);
			}
		}		
		//插入排序算法结束
		System.out.println("排序后：" + print(strArray));
	}
	//返回数组字符串
	public static String print(String[] strArray){
		StringBuilder string = new StringBuilder();
		for (String str : strArray) {
			string.append(str + "    ");
		}
		return string.toString();
	}
	//数据元素交换位置
	public static void exch(String[] strArray, int i, int j){
		String str = strArray[i];
		strArray[i] = strArray[j];
		strArray[j] = str;
	}
}
```
###### 运行结果
![代码运行结果](//img-blog.csdn.net/20180313170243865?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L3BlbmdsZWkxMjM0NTY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
