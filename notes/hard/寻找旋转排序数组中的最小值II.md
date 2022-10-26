# 寻找旋转排序数组中的最小值 II

## 原题链接

[154. 寻找旋转排序数组中的最小值 II - 力扣（LeetCode）](https://leetcode.cn/problems/find-minimum-in-rotated-sorted-array-ii/)

## 题解

~~~java
class Solution {
    public int findMin(int[] nums) {
        int l = 0, r = nums.length - 1;
        while(l < r){
            int mid = l + (r - l) / 2;
            if(nums[mid] < nums[r]){
                r = mid;
            }else if(nums[mid] > nums[r]){
                l = mid + 1;
            }else{
                --r;
            }
        }
        return nums[l];
    }
}
~~~