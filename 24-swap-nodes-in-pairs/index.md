# 24 Swap Nodes in Pairs



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

