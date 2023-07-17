# 两两交换链表中的节点


## Leetcode 24. 两两交换链表中的节点
给你一个链表，两两交换其中相邻的节点，并返回交换后链表的头节点。你必须在不修改节点内部的值的情况下完成本题（即，只能进行节点交换）。

<!--more-->

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def swapPairs(self, head: Optional[ListNode]) -> Optional[ListNode]:
        dummy_head = ListNode(next=head)
        current = dummy_head

        while current.next and current.next.next:
            # 保存第一个节点
            tmp = current.next
            # 保存第三个节点
            tmp_next = current.next.next.next

            # 头节点指向第二个节点
            current.next = current.next.next
            # 第二个节点指向第一个节点
            current.next.next = tmp
            # 第一个节点指向第三个节点
            tmp.next = tmp_next
            # 更新头节点位置
            current = tmp

        return dummy_head.next

```

