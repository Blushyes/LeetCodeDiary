# 环形链表 II

## 原题链接

[142. 环形链表 II - 力扣](https://leetcode.cn/problems/linked-list-cycle-ii/)

## 题解

~~~java
public class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode slow = head, fast = head;
        do{
            if(fast == null || fast.next == null) return null;
            slow = slow.next;   //慢指正走一步
            fast = fast.next.next;  //快指针走两步
        }while(slow != fast);
        fast = head;
        while(fast != slow){    //这次相遇时，快指针正好到环的入口
            fast = fast.next;	//此时令快指针慢下来
            slow = slow.next;
        }
        return fast;	//此时的相遇位置则为入口
    }
}
~~~

