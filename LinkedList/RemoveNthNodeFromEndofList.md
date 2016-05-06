###判断链表是否有环
[leetcode](https://leetcode.com/problems/linked-list-cycle/)

>题目
>给定一个链表，判断是否有环。

###解法
双指针法。
```java
public boolean hasCycle(ListNode head) 
{
         ListNode slow=head;
         ListNode fast=head;
         if(head==null)return false;
         while(fast.next!=null)
         {
             if(fast.next.next==null)
             {
	             return false;
             }
             
             slow=slow.next;
             fast=fast.next.next;     
             if(slow==fast)
             {
	             return true;
             }
         }
         return false;
      
}
```

