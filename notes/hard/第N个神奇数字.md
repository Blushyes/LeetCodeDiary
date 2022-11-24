# [第 N 个神奇数字](https://leetcode.cn/problems/nth-magical-number/)

~~~java
class Solution {
    public int nthMagicalNumber(int n, int a, int b) {
        int min = Math.min(a, b);
        long l = min;
        long r = (long)n * min;
        int c = lcm(a, b);
        while(l <= r){
            long mid = (l + r) / 2;
            long magic = mid / a + mid / b - mid / c;
            if(magic < n){
                l = mid + 1;
            }else{
                r = mid - 1;
            }
        }
        return (int)(l % 1000000007);
    }

    private int lcm(int a, int b) {
        return a * b / gcd(a, b);
    }

    private int gcd(int a, int b) {
        return b != 0 ? gcd(b, a % b) : a;
    }
}
~~~