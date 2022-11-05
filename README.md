# LeetCodeDiary
## 描述

LeetCode刷题日记，学习各种数据结构和算法，记录一下刷题过程。

# 整理

## 二分查找
[二分查找](./notes/easy/二分查找.md)，

[猜数字大小](./notes/easy/猜数字大小.md)，

[搜索插入位置](./notes/easy/搜索插入位置.md)，

[在排序数组中查找元素的第一个和最后一个位置](./notes/medium/在排序数组中查找元素的第一个和最后一个位置.md)，

[Two Sum](./notes/medium/两数和.md)，

[寻找旋转排序数组中的最小值](./notes/medium/寻找旋转排序数组中的最小值.md)，

[寻找旋转排序数组中的最小值II](./notes/
hard/寻找旋转排序数组中的最小值II.md)，

[搜索旋转排序数组](./notes/medium/搜索旋转排序数组.md)，

[搜索旋转排序数组 II](https://leetcode.cn/problems/search-in-rotated-sorted-array-ii/)，

[第一个错误的版本](./notes/easy/第一个错误的版本.md)，

[寻找峰值](https://leetcode.cn/problems/find-peak-element/)，

[x的平方根](./notes/easy/x的平方根.md)，

[有效的完全平方数](./notes/easy/有效的完全平方数.md)，

[Pow](./notes/medium/Pow.md)，

[转变数组后最接近目标值的数组和](./notes/medium/转变数组后最接近目标值的数组和.md)，

[爱吃香蕉的珂珂](./notes/medium/爱吃香蕉的珂珂.md)，

## 双指针
[Two Sum](./notes/medium/两数和.md)，

[合并两个有序数组](./notes/easy/合并两个有序数组.md)，

[接雨水](./notes/hard/接雨水.md)

## 贪心
[把数组排成最小的数](./notes/medium/把数组排成最小的数.md)

## 链表
[反转链表](./notes/easy/反转链表.md)，

[相交链表](./notes/easy/相交链表.md)，

[合并两个排序的链表](./notes/easy/合并两个排序的链表.md)，

[分隔链表](./notes/medium/分隔链表.md)，

[环形链表II](./notes/medium/环形链表II.md)，

[分隔链表](./notes/medium/分隔链表.md)，

[反转链表II](./notes/medium/反转链表II.md)，

[复制带随机指针的链表](./notes/medium/复制带随机指针的链表.md)

## 栈
[有效的括号](./notes/easy/有效的括号.md)，

[基本计算机](./notes/hard/基本计算机.md)，

[最小栈](./notes/medium/最小栈.md)，

[验证栈序列](./notes/medium/验证栈序列.md)，

[每日温度](./notes/medium/每日温度.md)，

[接雨水](./notes/hard/接雨水.md)

## 动态规划：
[接雨水](./notes/hard/接雨水.md)，

[杨辉三角II](./notes/easy/杨辉三角II.md)，

[打家劫舍](./notes/medium/打家劫舍.md)

## List

[杨辉三角](./notes/easy/杨辉三角.md)，

# 总结

## 栈

### 关于单调栈

+ **单调栈的介绍**

  > ​	**单调栈（monotone-stack）是指栈内元素（栈底到栈顶）都是（严格）单调递增或者单调递减的。**

+ **什么时候用**

  + **当需要找左边或右边第一个比自己大/小的位置用单调栈。**

  + 例如[每日温度](./notes/medium/每日温度.md)中寻找右边比当前温度更高的温度。

## 关于二分查找的一些总结

+ **二分查找虽然思路简单，但是在细节上却有些复杂**，这也导致在写二分查找的时候经常出错，例如出现无限循环的超时错误或者是各种各样的解答出错，无非就是细节方面没有处理好。
+ 二分查找有两种查找类型，**一种是具体查找**，**一种是模糊查找**。
+ 一种是具体知道是要查找的对象是谁，例如[二分查找](./notes/easy/二分查找.md)中就是**有一个明确的target**，这种则使用在循环体内部判断相等然后返回的方式（这种方式的循环条件一般为left<=right），若出循环则返回未查找到的标志；而像[寻找旋转排序数组中的最小值](./notes/medium/寻找旋转排序数组中的最小值.md)中则**不知道具体要寻找的数是什么，只是一个比较模糊的搜索**，知道要查找的对象的一些性质，这种的话则一般使用排除区间最后当left和right重合时就是要查找的对象（这种一般都是使用left<right）。

# 典型题（有详解）

## 动态规划

[打家劫舍](./notes/medium/打家劫舍.md)

# Tracks

+ **二分查找真的是细节狂魔！！！**
+ **二分查找查找的数组不一定是严格单调**
+ **要是Java能重载运算符就好了，ArrayList的get和set真的麻烦！**