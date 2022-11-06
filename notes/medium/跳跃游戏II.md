# [跳跃游戏 II](https://leetcode.cn/problems/jump-game-ii/)

# 动态规划

~~~java
class Solution {
    public int jump(int[] nums) {
        int n = nums.length;
        if(n == 1) return 0;
        //定义状态为从0位置跳到当前位置所需要的最少次数
        int[] dp = new int[n];
        dp[0] = 0;
        //开始迭代dp表，状态转移方程为dp[i] = min{j∈[0,i)|从0开始花最小次数跳到j然后一步跳到i的次数}
        for(int i = 1; i < n; ++i){
            int min = Integer.MAX_VALUE;
            for(int j = 0; j < i; ++j){
                if(j + nums[j] >= i){
                    min = Math.min(min, 1 + dp[j]);
                }
            }
            dp[i] = min;
        }
        return dp[n - 1];
    }
}
~~~

**状态：从0位置跳到当前位置所需要的最少次数**

**状态转移方程：*dp[i] = min{j∈[0,i)|dp[j] + 1*}**

# 贪心

~~~java
class Solution {
    public int jump(int[] nums) {
        int n = nums.length;
        //记录当前所能到达的最远距离
        int furthest = 0;
        //记录落点区间尾部
        int end = 0;
        //记录跳跃次数
        int steps = 0;
        //注意不能遍历最后一个元素，因为这样当end为最后一个元素的时候，可能就会导致增加一次多余的跳跃
        for(int i = 0; i < n - 1; ++i){
            //维护跳跃的最远距离
            furthest = Math.max(nums[i] + i, furthest);
            //如果遍历到end，说明该选择落点也就是下一步的起跳点了
            if(i == end){
                //延长落点区间尾部，扩大落点范围为当前能跳到的最远距离
                end = furthest;
                //跳跃一次但不选择落点即下一次的起跳点，只是知道落点肯定不会远于end
                ++steps;
            }
        }
        return steps;
    }
}
~~~

