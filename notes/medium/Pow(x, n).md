# [Pow(x, n)](https://leetcode.cn/problems/powx-n/)

## 题解

~~~java
class Solution {
    public double myPow(double x, long n) {
        if(n == 0){
            return 1.0;
        }
        if(n < 0){
            return 1 / myPow(x, -n);
        }
        //先记录y的值，不然myPow(x, n / 2) * myPow(x, n / 2)就需要递归两次
        double y = myPow(x, n / 2);
        //单数要多乘一次x
        return n == 1 ? x : n % 2 == 0 ? y * y : y * y * x;
    }
}
~~~