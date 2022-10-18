# 两数和（Two Sum）

## 原题链接

[167. 两数之和 II - 输入有序数组 - 力扣](https://leetcode.cn/problems/two-sum-ii-input-array-is-sorted/)

## 代码

~~~java
public int[] twoSum(int[] numbers, int target) {
	int l = 0, r = numbers.length - 1;
	while (l < r) {
		int sum = numbers[l] + numbers[r];
		if (sum == target) break;
		else if (sum < target) ++l;
		else --r;
	}
	return new int[] {l + 1, r + 1};
}
~~~

## 总结

其实就是遍历思想，只不过简单遍历时间复杂度为O(n<sup>2</sup>)，而利用双指针可以做到O(n)。

还有简单遍历其实也是两个指针，不过两个指针分别在单独的遍历上，而不是像双指针同时处于同一个遍历。

这里附上简单遍历代码：

~~~java
for (int p1 = 0; p1 < numbers.length; ++p1) {
	for (int p2 = 0; p2 < numbers.length; ++p2) {
		if (p1 != p2 && numbers[p1] + numbers[p2] == target) return new int[] {p1 + 1, p2 + 1};
	}
}
return null;
~~~



这里对比一下运行结果就很容易发现：

| 提交结果                                                  | 执行用时 | 内存消耗 | 语言 | 提交时间         | 备注     |
| :-------------------------------------------------------- | :------- | :------- | :--- | :--------------- | :------- |
| [通过](https://leetcode.cn/submissions/detail/374144236/) | 1 ms     | 44.5 MB  | Java | 2022/10/18 14:19 | 双指针   |
| [通过](https://leetcode.cn/submissions/detail/374144086/) | 899 ms   | 44 MB    | Java | 2022/10/18 14:19 | 简单遍历 |