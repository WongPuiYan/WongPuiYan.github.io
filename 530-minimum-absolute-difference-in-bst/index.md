# 二叉搜索树的最小绝对差


## 530. 二叉搜索树的最小绝对差
给你一个二叉搜索树的根节点 root ，返回 树中任意两不同节点值之间的最小差值 。
差值是一个正数，其数值等于两值之差的绝对值。

<!--more-->

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

# 中序
class Solution:
    def __init__(self):
        self.vec = []

    def traversal(self, node):
        if node is None:
            return

        self.traversal(node.left)
        self.vec.append(node.val)
        self.traversal(node.right)

    def getMinimumDifference(self, root: Optional[TreeNode]) -> int:
        self.vec = []
        self.traversal(root)

        if len(self.vec) < 2:
            return 0

        result = float("inf")

        for i in range(1, len(self.vec)):
            result = min(result, self.vec[i] - self.vec[i - 1])

        return result

# 中序
class Solution:
    def __init__(self):
        self.result = float("inf")
        self.pre = None

    def traversal(self, node: Optional[TreeNode]) -> None:
        if node is None:
            return

        self.traversal(node.left)

        if self.pre is not None:
            self.result = min(self.result, node.val - self.pre.val)
        self.pre = node

        self.traversal(node.right)

    def getMinimumDifference(self, root: Optional[TreeNode]) -> int:
        self.traversal(root)

        return self.result

# 迭代
class Solution:
    def getMinimumDifference(self, root: Optional[TreeNode]) -> int:
        stack = []
        cur = root
        pre = None
        res = float("inf")

        while cur is not None or len(stack) > 0:
            if cur is not None:
                stack.append(cur)
                cur = cur.left
            else:
                cur = stack.pop()

                if pre is not None:
                    res = min(res, cur.val - pre.val)

                pre = cur
                cur = cur.right

        return res

```

