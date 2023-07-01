# 移除链表元素


## leetcode 203. 移除链表元素
给你一个链表的头节点 head 和一个整数 val ，请你删除链表中所有满足 Node.val == val 的节点，并返回 新的头节点 。

<!--more-->

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeElements(self, head: ListNode, val: int) -> ListNode:
        p_h = ListNode()
        p_h.next = head
        p = p_h
        while p:
            if p.next and p.next.val == val:
                p.next = p.next.next
            else:
                p = p.next
        return p_h.next

```
