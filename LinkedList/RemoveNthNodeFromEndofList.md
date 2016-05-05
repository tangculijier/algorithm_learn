#移除链表中第n个节点
来源[leetcode](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

####给定一个链表。移除它的第n个节点并返回头节点。
比如: 
1->2->3->4->5（n = 2），n总是有效的
result: 1->2->3->5.
>**Note:**尝试用O(1)时间复杂度  

-----

####解法1
找到第n个节点删除。
```java
/**
 * Definition for singly-linked list.
 * public class ListNode 
 * {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) 
 *    {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution
 {
    public ListNode removeNthFromEnd(ListNode head, int n) 
    {
        if(head==null)return null;
            ListNode current = head;
            int length = 0;
            while(current != null)
            {
                current = current.next;
                length++;
            }
          if(n == 1 && length ==1) return null;
            if(n == length) return head.next;
            current = head;
            for(int i = 0 ; i < length - n - 1; i++)
            {
                current = current.next;
            }
            current.next = current.next.next;
            return head;
        
            
        
    }
}
```  

--------
####解法2
连个指针，一个先行n个位置，到达后两个同时出发，先指针为null时表示走到链表结束，另一个指针走到第n节点。

```java
public class Solution 
{
    public ListNode removeNthFromEnd(ListNode head, int n) 
    {
	       if(n == 0 || head == null)
	       {  
                return head;  
            }  
            if(n == 1 && head.next==null)
            {  
                return null;  
            }  
               
            ListNode p = head, q = head;  
            // 让p先行q n个位置  
            for(int i=0; i<n; i++)
            {  
                if(p != null)
                {  
                    p = p.next;  
                }else
                {  
                    return head;  
                }  
            }  
               
            // 如果这个时候p已经是null，则说明删除的必定为head  
            if(p == null)
            {  
                head = head.next;  
                return head;  
            }  
               
            // p和q一起前进  
            while(p.next != null)
            {  
                q = q.next;  
                p = p.next;  
            }  
            // 删除元素  
            q.next = q.next.next;  
            return head;
    }
}
```

