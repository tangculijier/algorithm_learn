
###合并数组并排序
[leetcode](https://leetcode.com/problems/merge-sorted-array/)
Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.
给两个已经排序好的数组num1,num2，合并数组并排序。
>**注意:**假设num1有足够的控件容纳num1、num2长度之和。m是num1的长度，n是num2的长度。

------
####优解法：
```java
public class Solution 
{
    public void merge(int A[], int m, int B[], int n) 
    {
        int i=m-1;
        int j=n-1;
        int k=m+n-1;
        
        while(i>=0 && j>=0)
        {
            A[k--] = A[i] > B[j] ? A[i--] : B[j--]; 
        }
        while(j>=0) 
        {
            A[k--] = B[j--];
        }
    }
}
```

