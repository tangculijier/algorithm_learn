###数组中寻找出现2次的数
[leetcode](https://leetcode.com/problems/single-number/)
>题目：给定一个数组，每个数字都出现过一次，只有一个出现过2次，找出那个数。


-----
####解法1
构造出一个Map，key=数字，value=出现次数。
```java
public class Solution
{
    public int singleNumber(int[] A)
    {
       Map<Integer, Integer> map = new HashMap<Integer, Integer>();  
     if(A.length == 0 || A == null)
     {  
         return 0;  
     }  
     for(int i=0;i<A.length;i++)
     {  
         if(map.containsKey(A[i]))
         {  
             int value = map.get(A[i]);  
             map.put(A[i], value+1);  
         }
         else
         {  
             map.put(A[i], 1);  
         }  
     }  
     for(int i=0;i<A.length;i++)
     {  
         int value = map.get(A[i]);  
         if(value == 1)
         {  
             return A[i];  
         }  
     }  
     return 0;  
    }
}
```
####解法2
使用异或：相同为0 不同为1
0和a数异或都是a
a和a异或就是0
由于每个数有两个 所以总会相见一次 所以还是0
```java
public static int singleNumber(int[] A)
{
        int res = 0;
        for (int i : A)
        {
            res ^= i;
        }
        return res;
    }
```


