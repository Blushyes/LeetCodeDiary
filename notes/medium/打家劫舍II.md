# [打家劫舍 II](https://leetcode.cn/problems/house-robber-ii/)

# 动态规划

本题就是在打家劫舍的基础上进行分类讨论而已，我们定义一个辅助函数，传入一个参数stealHead来判断是否将数组首元素考虑在决策内。

头部和尾部只有三种决策可能：

+ **偷头不偷尾**
+ **偷尾不偷头**
+ **头尾都不偷**

可以看出首尾元素不能同时考虑，但是必须都要考虑。

那么就可以分为两种情况：

+ 考虑将首元素放在决策范围（决定是否要偷），将尾元素排除出决策范围，头尾决策结果：**偷头不偷尾 or 头尾都不偷**
+ 不考虑将首元素放在决策范围，同时要将尾元素考虑在内，头尾决策结果：**偷尾不偷头 or 头尾都不偷**

这样两种情况加在一起就能组成一个完整的情况。

~~~java
class Solution {
    public int rob(int[] nums) {
        int n = nums.length;
        if(n == 1) return nums[0];
        if(n == 2) return Math.max(nums[n - 1], nums[n - 2]);
        //在两种决策中选出最优的
        return Math.max(helper(nums, true), helper(nums, false));
    }

    private int helper(int[] nums, boolean stealHead){
        //若考虑首元素则不考虑尾元素
        int n = stealHead ? nums.length - 1 : nums.length;
        int pre = nums[n - 1];
        int curr = Math.max(nums[n - 1], nums[n - 2]);
        //若考虑首元素则遍历到0为止，不考虑就不遍历到0
        for(int i = n - 3; i >= (stealHead ? 0 : 1); --i){
            int tmp = curr;
            curr = Math.max(nums[i] + pre, curr);
            pre = tmp;
        }
        return curr;
    }
}
~~~
