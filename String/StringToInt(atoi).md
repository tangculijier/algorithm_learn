#String转为Int(atoi)
来自[leetcode](https://leetcode.com/problems/string-to-integer-atoi/)

经常在面试时候见到这种题，题目虽小，但是五脏俱全，考察各方面的编程技巧。
需要考察的方面有：
- [x] 输入异常
- [x] 正负号
- [x] string常用函数
- [x] 溢出
- [x] 函数边界


---
解答：
```java
public class Solution {
    public int myAtoi(String str) {
          if(str == null || str.length() ==0 ) return 0;
          str = str.trim();
          boolean isPositive = true;
          boolean isOverFloew = false;
          long res = 0;
          for(int i = 0 ; i < str.length(); i++)
          {
               char ch = str.charAt(i);
               if(i ==0 && (ch == '-' || ch == '+'))
               {
                    if(ch == '-')
                    {
                         isPositive = false;
                    }
                    continue;
               }
               if(ch > '9' || ch < '0')  break;//"+-2"  " -0012a42"
               res = res * 10 + (ch - '0');
               if( res >  Integer.MAX_VALUE)
                    isOverFloew = true;
          }
          res = isPositive == true ? res : -res;
         
          if( isOverFloew == true &&  isPositive == true )
               return  Integer.MAX_VALUE;
          else if(isOverFloew == true &&  isPositive == false )
               return  Integer.MIN_VALUE;
          else
          return (int) res;
    }
}

```

