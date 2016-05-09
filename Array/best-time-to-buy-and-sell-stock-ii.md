###卖股票的最佳时2 -（可以交易多次）
[leetcode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)
>题目：
>给出一个月的股票价格（数组形式）。
>假设你现在是交易员，已知这个月的股票的价格，设计一个算法一买一卖可以得到的最大利润。(可以交易多次)

-----
**解法**

```java
public int maxProfit(int[] prices) 
{
        if (prices.length < 2) return 0;
        int maxProfit = 0;
        for (int i = 1; i < prices.length; i++)
        {
            int diff = prices[i] - prices[i - 1];
            if (diff > 0) 
            {
                maxProfit += diff;
            }
        }
        
        return maxProfit;
    }
```

