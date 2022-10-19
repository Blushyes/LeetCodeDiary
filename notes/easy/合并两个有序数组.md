# 合并两个有序数组（Merge Sorted Array）

## 原题链接

[88. 合并两个有序数组 - 力扣（LeetCode）](https://leetcode.cn/problems/merge-sorted-array/)

## 代码

~~~java
public void merge(int[] nums1, int m, int[] nums2, int n) {
	int p = m-- + n-- - 1;
	while (m >= 0 && n >= 0) {
		nums1[p--] = nums1[m] > nums2[n] ? nums1[m--] : nums2[n--];
	}
	while (n >= 0) {
		nums1[p--] = nums2[n--];
	}
}
~~~

## 总结

刚开始一看到这道题第一想法就是从后往前遍历，只不过不知道为什么又取消了这个想法，后来从前面是在想着麻烦（还要各种交换各种排序），才去看了看答案，果然还是从后面往前面遍历比较简单。

这道题的两个指针本质上也属于同一次遍历。