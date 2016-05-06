###Ѱ�������������λ��
from [leetcode](https://leetcode.com/problems/median-of-two-sorted-arrays/)

>��Ŀ
>�������Ѿ�����õ����飬���ȷֱ���m��n��Ҫ���ҳ��ں���������������λ����
>�����O(log(m+n))ʱ�临�Ӷ�����ɡ�

-----

####�ⷨ1
�����ںϲ�����Ч�����ģ�����Ҳ����������
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
####�ⷨ2
ʹ������ָ�����򣬱���һ��Ч�����˸��ơ�
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
####�ⷨ3
�ο�[ Median of Two Sorted Arrays](http://blog.csdn.net/zxzxy1988/article/details/8587244) ʹ������ָ������,Ч�ʿ��ԴﵽO(log(m+n))��

**����˼�룺**
�÷����ĺ����ǽ�ԭ����ת���һ��Ѱ�ҵ�kС�������⣨��������ԭ�����������У���������λ��ʵ�����ǵ�(m+n)/2С������
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
