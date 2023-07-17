# 找树左下角的值


## Leetcode 513. 找树左下角的值
给定一个二叉树的 根节点 root，请找出该二叉树的 最底层 最左边 节点的值。
假设二叉树中至少有一个节点。

<!--more-->

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

# 递归
class Solution:
    def traversal(self, node: TreeNode, depth: int) -> None:
        if not node.left and not node.right:
            if depth > self.max_depth:
                self.max_depth = depth
                self.result = node.val
            return

        if node.left:
            self.traversal(node.left, depth + 1)

        if node.right:
            self.traversal(node.right, depth + 1)

    def findBottomLeftValue(self, root: Optional[TreeNode]) -> int:
        self.max_depth = float("-inf")
        self.result = None
        self.traversal(root, 0)

        return self.result

class Solution:
    def findBottomLeftValue(self, root: Optional[TreeNode]) -> int:
        if root is None:
            return 0

        queue = collections.deque()
        queue.append(root)
        result = 0

        while queue:
            for i in range(len(queue)):
                node = queue.popleft()

                if i == 0:
                    result = node.val

                if node.left:
                    queue.append(node.left)

                if node.right:
                    queue.append(node.right)

        return result
            
```

