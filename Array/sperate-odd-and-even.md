###将整数数组按就分成2个部分，数组坐标为奇数，右边为偶数
>题目：输入一个数组，实现一个函数来调整该数组中的数字顺序。使得所有奇数位于前半部分，所有偶数位于后半部分。

------

**解法：**
维护两个指针，一个在前一个在后，前面的遇到偶数停，后面的遇到奇数停，然后互换，知道前后指针相遇。
```java
public static void sperateOddAndEven(int[] a)
{
        int i=0;//定义左指针下标
        int j=a.length-1;//定义右指针下标
        int temp;
        while(i<j)
        {
            while(a[i]%2!=0)//如果左边遇到奇数则继续遍历
                i++;
            while(a[j]%2==0)//同理右边
                j--;
            
            if(i<j)//swap
            {
                temp=a[i];
                a[i]=a[j];
                a[j]=temp;
            }
        }
    }
```
-----

