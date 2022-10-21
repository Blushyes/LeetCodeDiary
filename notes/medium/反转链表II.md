# 反转链表 II

## 原题链接

[92. 反转链表 II - 力扣](https://leetcode.cn/problems/reverse-linked-list-ii/)

## 题解

~~~java
class Solution {
    public ListNode reverseBetween(ListNode head, int left, int right) {
        // 因为头节点有可能发生变化，使用虚拟头节点可以避免复杂的分类讨论
        ListNode dummyNode = new ListNode(-1);
        dummyNode.next = head;

        ListNode pre = dummyNode;
        // 第 1 步：从虚拟头节点走 left - 1 步，来到 left 节点的前一个节点
        // 建议写在 for 循环里，语义清晰
        for (int i = 0; i < left - 1; i++) {
            pre = pre.next;
        }

        // 第 2 步：从 pre 再走 right - left + 1 步，来到 right 节点
        ListNode rightNode = pre;
        for (int i = 0; i < right - left + 1; i++) {
            rightNode = rightNode.next;
        }

        // 第 3 步：切断出一个子链表（截取链表）
        ListNode leftNode = pre.next;
        ListNode curr = rightNode.next;

        // 注意：切断链接
        pre.next = null;
        rightNode.next = null;

        // 第 4 步：同第 206 题，反转链表的子区间
        reverseLinkedList(leftNode);

        // 第 5 步：接回到原来的链表中
        pre.next = rightNode;
        leftNode.next = curr;
        return dummyNode.next;
    }

    private void reverseLinkedList(ListNode head) {
        // 也可以使用递归反转一个链表
        ListNode pre = null;
        ListNode cur = head;

        while (cur != null) {
            ListNode next = cur.next;
            cur.next = pre;
            pre = cur;
            cur = next;
        }
    }
}
~~~

此为官方解，这题思路简单但是操作起来容易出错。

~~~java
class Solution {
    private void reverseLinkedList(ListNode head) {
        ListNode pre = null;
        ListNode cur = head;

        while (cur != null) {
            ListNode next = cur.next;
            cur.next = pre;
            pre = cur;
            cur = next;
        }
    }

    public ListNode reverseBetween(ListNode head, int left, int right) {
        ListNode dummyNode = new ListNode(-1, head);
        ListNode cut = dummyNode, linkNode1, linkNode2;

        for(int i = 0; i < left - 1; ++i){
            cut = cut.next;
        }
        ListNode tail = cut.next;
        linkNode1 = cut;

        for(int i = left - 1; i < right; ++i){
            cut = cut.next;
        }
        linkNode2 = cut.next;

        linkNode1.next = null;
        cut.next = null;

        reverseLinkedList(tail);

        tail.next = linkNode2;
        linkNode1.next = cut;

        return dummyNode.next;
    }
}
~~~

此为按照官方解修改后的解。