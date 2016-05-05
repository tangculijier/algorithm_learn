###翻转元音字符串
来源[leetcode-Reverse Vowels of a String](https://leetcode.com/problems/reverse-vowels-of-a-string/)
>题目：Given s = "hello", return "holle".     Given s = "leetcode", return "leotcede".

------
**解法**
一般翻转字符串可以用java内置方法
```java
	new StringBuilder(inputStr).reverse().toString();
```
这个题的要求是只翻转元音字母"aeiou",所以可以采用双指针方法

**需要注意**
 - [x] 输入异常
 - [x] 指针边界
 - [x] 交换条件
 
```java
	   String vowels = "aoeiuAOEIU";
       char[] a = s.toCharArray();
       int i = 0;//left pointer
       int j = a.length - i - 1;//right pointer
       while (i < j)
        {
           while (i < j && !vowels.contains(a[i] + ""))
           {
               i++;
           }
           while (i < j && !vowels.contains(a[j] + "")) 
           {
               j--;
           }
           if (i < j) 
           {
               char c = a[i];
               a[i++] = a[j];
               a[j--] = c;
           }
       }

       return new String(a);
	        
	 
```


