###将数字转成罗马数字
[leetcode](https://leetcode.com/problems/integer-to-roman/)
>题目:
>给出一个integer,把它转成一个罗马数字。
>输入从1-3999.

-----
**解法**
将value和罗马数字一次对应，然后依次相减。
```java
public String intToRoman(int num) 
{
       int[] values={1000,900,500,400,100,90,50,40,10,9,5,4,1};
        String[] roman={"M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"};
        String result="";
        for(int i=0;i<values.length;i++)
        {
            while(num-values[i]>=0)
            {
                num-=values[i];
                result+=roman[i];
            }
            
        }
        return result;
    }

```

