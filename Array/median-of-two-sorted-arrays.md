###寻找两个数组的中位数
from [leetcode](https://leetcode.com/problems/median-of-two-sorted-arrays/)

>题目
>有两个已经排序好的数组，长度分别是m和n。要求找出融合这两个数组后的中位数。
>最好再O(log(m+n))时间复杂度内完成。

-----

####解法1
暴力融合并排序，效率最差的，但是也能做出来。
```java
public static double findMedianSortedArrays(int A[], int B[]) 
{
	    int[] d3 = new int[A.length + B.length];
	    System.arraycopy(A, 0, d3, 0, A.length);
	    System.arraycopy(B, 0, d3, A.length, B.length);
	    Arrays.sort(d3);
	    return d3.length%2!=0?d3[d3.length/2]/1.0:(d3[d3.length/2-1]+d3[d3.length/2])/2.0;
           
 }
```

----
####解法2
使用两个指针排序，比上一个效率有了改善。
```java
  private static double findMedianSortedArrays(int[] a, int[] b) {
        int k=a.length+b.length;
        int[] c=new int[k];
        int i=0,j=0,m=0;
        while(m!=k)
        {
            if(i==a.length)
            {
                c[m]=b[j];
                j++;
                
            }
            else if(j==b.length)
            {
                c[m]=a[i];
                i++;
            }
            else if(a[i]<b[j])
            {
                c[m]=a[i];
                i++;
            
            }
            else 
            {
                c[m]=b[j];
                j++;
                
                
            }
            m++;
        }
        
        return k%2==0?(c[k/2-1]+c[k/2])/2.0:c[k/2]/1.0;
        
    }

```
----
####解法3
参考[ Median of Two Sorted Arrays](http://blog.csdn.net/zxzxy1988/article/details/8587244) 使用两个指针排序,效率可以达到O(log(m+n))。

**核心思想：**
该方法的核心是将原问题转变成一个寻找第k小数的问题（假设两个原序列升序排列），这样中位数实际上是第(m+n)/2小的数。
```cpp
  double findKth(int a[], int m, int b[], int n, int k)
{
	//always assume that m is equal or smaller than n
	if (m > n)
		return findKth(b, n, a, m, k);
	if (m == 0)
		return b[k - 1];
	if (k == 1)
		return min(a[0], b[0]);
	//divide k into two parts
	int pa = min(k / 2, m), pb = k - pa;
	if (a[pa - 1] < b[pb - 1])
		return findKth(a + pa, m - pa, b, n, k - pa);
	else if (a[pa - 1] > b[pb - 1])
		return findKth(a, m, b + pb, n - pb, k - pb);
	else
		return a[pa - 1];
}

class Solution
{
public:
	double findMedianSortedArrays(int A[], int m, int B[], int n)
	{
		int total = m + n;
		if (total & 0x1)
			return findKth(A, m, B, n, total / 2 + 1);
		else
			return (findKth(A, m, B, n, total / 2)
					+ findKth(A, m, B, n, total / 2 + 1)) / 2;
	}
};
```
