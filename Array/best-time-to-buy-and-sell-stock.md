###卖股票的最佳时间
[leetcode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
>题目：
>给出一个月的股票价格（数组形式）。
>假设你现在是交易员，已知这个月的股票的价格，设计一个算法一买一卖可以得到的最大利润。

-----
**解法**  

需要注意的是，卖的时间肯定在买的时间之后。
遍历一遍数组，首先将最低价设为prices[0],然后开始比较，发现最大收益就替换，发现最低价也替换。

```java
public int maxProfit(int[] prices)
 {
         if(prices.length==0)return 0;
         int maxProfit=0;
         int min=prices[0];
         for(int i=0;i<prices.length;i++)
         {
             maxProfit=prices[i]-min>maxProfit?prices[i]-min:maxProfit;
             min=prices[i]<min?prices[i]:min;
         }      
         return maxProfit;
   
     } 
```

