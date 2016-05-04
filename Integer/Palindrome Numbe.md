#判断一个数字是否是回文数，尝试不用其他额外空间。
来源[leetcode](https://leetcode.com/problems/palindrome-number/)

**注意：**  
1. 负数也有可能成为回文数吗？  
2. 如果你想让int转为string，注意不用其他空间这个约束。  
3. 你也可以翻转一个int，但是有可能会溢出。  
 ----
解法:
```java
 public class Solution 
{
    public boolean isPalindrome(int x)
     {
        if(x<0) return false;
		int temp = x, reverseX = 0; 
        while (temp > 0) 
        { 
            reverseX = reverseX * 10 + temp % 10; 
            temp /= 10; 
        } 
        return x == reverseX; 
    }
}
```
