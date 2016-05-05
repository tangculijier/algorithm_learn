###��תԪ���ַ���
��Դ[leetcode-Reverse Vowels of a String](https://leetcode.com/problems/reverse-vowels-of-a-string/)
>��Ŀ��Given s = "hello", return "holle".     Given s = "leetcode", return "leotcede".

------
**�ⷨ**
һ�㷭ת�ַ���������java���÷���
```java
	new StringBuilder(inputStr).reverse().toString();
```
������Ҫ����ֻ��תԪ����ĸ"aeiou",���Կ��Բ���˫ָ�뷽��

**��Ҫע��**
 - [x] �����쳣
 - [x] ָ��߽�
 - [x] ��������
 
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


