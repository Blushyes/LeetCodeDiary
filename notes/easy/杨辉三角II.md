# [杨辉三角 II](https://leetcode.cn/problems/pascals-triangle-ii/)

## 递归

~~~java
class Solution {
    public List<Integer> getRow(int rowIndex) {
        //递归基
        if(rowIndex == 0){
            return List.of(1);
        }
        List<Integer> ans = new ArrayList<Integer>();
        //通过递归获取上一行
        List<Integer> upper = getRow(rowIndex - 1);
        for(int i = 0; i < rowIndex + 1; ++i){
            if(i == 0 || i == rowIndex){
                ans.add(1);
            }else{
                ans.add(upper.get(i - 1) + upper.get(i));
            }
        }
        return ans;
    }
}
~~~

## 动态规划

+ 首先定义状态：

>  ***dp\[m][n]***：杨辉三角表中的第m行第n列的数

+ 确定状态转移方程：

> n == 0 or n == rowIndex（首尾）： 
>
> ***dp\[m][n] = 1;***
>
> else： 
>
> ***dp\[m][n] = dp\[m - 1][n - 1] + dp\[m - 1][n]***

+ 具体实现如下：

~~~java
class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<List<Integer>> dp = new ArrayList<List<Integer>>();
        for(int i = 0; i <= rowIndex; ++i){
            List<Integer> row = new ArrayList<Integer>();
            for(int j = 0; j <= i; ++j){
                if(j == 0 || j == i){
                    row.add(1);
                }else{
                    row.add(dp.get(i - 1).get(j - 1) + dp.get(i - 1).get(j));
                }
            }
            dp.add(row);
        }
        return dp.get(rowIndex);
    }
}
~~~

当然动态规划还有两种优化方案，详细看官方题解。