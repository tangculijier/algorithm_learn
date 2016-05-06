###找出数组中最大和的连续字串
[leetcode](https://leetcode.com/problems/maximum-subarray/)
>题目  
>Find the contiguous subarray within an array (containing at least one number) which has the largest sum.
>For example, given the array [−2,1,−3,4,−1,2,1,−5,4],
>the contiguous subarray [4,−1,2,1] has the largest sum = 6.

----
####解法1:
暴力搜索！
```java
public static int maxSubArray(int[] A) 
{
            int max=A[0];
            for(int i=0;i<A.length;i++)
            {
                int sum=0;
                for(int j=i;j<A.length;j++)
                {
                    sum+=A[j];
                    if(sum>max)
                    {
	                     max=sum;
					}                       
            }
                
         return max;
      }
```
####解法2:
如果和<0以后就重新算。
```java
public static int maxSubArray(int[] A) 
{
         int max=A[0];
         int sum=0;
         for(int i=0;i<A.length;i++)
         {
             sum+=A[i];
             if(sum>max)
                 max=sum;
             
             if(sum<0)
             sum=0;
         }
         return max;
}
```

