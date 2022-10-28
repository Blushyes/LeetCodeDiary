# [x 的平方根 ](https://leetcode.cn/problems/sqrtx/)

## 题解

~~~java
class Solution {
    public int mySqrt(int x) {
        int l = 1, r = x;
        if(x == 0){
            return x;
        }
        while(l <= r){
            int mid = l + (r - l) / 2;
            int sqrt_x =  x / mid;
            if(sqrt_x == mid){
                return sqrt_x;
            }else if(sqrt_x < mid){
                r = mid - 1;
            }else{
                l = mid + 1;
            }
        }
        return r;
    }
}
~~~

~~~java
class Solution {
    public int mySqrt(int x) {
        int l = 1, r = x;
        if(x == 0){
            return x;
        }
        while(l <= r){
            int mid = l + (r - l) / 2;
            long mid_2 =  (long)mid * mid;
            if(mid_2 == x){
                return mid;
            }else if(mid_2 > x){
                r = mid - 1;
            }else{
                l = mid + 1;
            }
        }
        return r;
    }
}
~~~