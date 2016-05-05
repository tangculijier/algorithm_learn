#java中数组copy的方法使用
-------------
###1.  Arrays.copy(original,newLength)
```java
public static int[] copyOf(int[] original, int newLength)
{
    int[] copy = new int[newLength];
     System.arraycopy(original, 0, copy, 0,Math.min(original.length, newLength));
     return copy;
}
```
    
首先new一个新数组 然后copy过去 return这个新数组
```java
int[] strArray = new int[] {1,2,3,4};
int[] copyArray=Arrays.copyOf(strArray,2);//result:{1,2}
```
结果copyArray就是
```java
int[] strArray = new int[] {1,2,3,4};
int[] copyArray=Arrays.copyOf(strArray,10);//result:{1,2,3,4,0,0,0,0,0,0}
```
不会报错 因为最后的数组总是按后面那个newLength规定的新数组来说 


###2.  System.arraycopy(src,srcPos,dest,destPos,length)
```java
/**
* @param      src      the source array.源数组；
* @param      srcPos   starting position in the source array.源数组要复制的起始位置
* @param      dest     the destination array.目的数组；
* @param      destPos  starting position in the destination data.目的数组放置的起始位置；
* @param      length   the number of array elements to be copied.复制的长度
**/
public static native void arraycopy(Object src,int srcPos,Object dest,int destPos, int length);
```


- 例子1:  
```java
int[] srcArray = new int[] {1,2,3,4};
int[] destArray = new int[4];
System.arraycopy(srcArray , 0, destArray , 0, 3);//result:{1,2,3,0}
```
- 例子2：  
```java
int[] srcArray = new int[] {1,2,3,4};
int[] destArray = new int[4];
System.arraycopy(srcArray , 0, destArray , 0, 5);直接错:java.lang.ArrayIndexOutOfBoundsException
//复制的长度超过了原来的数组长度
```

 **注意它是个native方法**，具体的源码分析见[System.arraycopy源码分析](http://www.360doc.com/content/14/0713/19/1073512_394157835.shtml)



 

