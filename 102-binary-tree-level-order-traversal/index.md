# 二叉树的层序遍历


## 102. 二叉树的层序遍历
给你二叉树的根节点 root ，返回其节点值的 层序遍历 。 （即逐层地，从左到右访问所有节点）。

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
    def helper(self, node: Optional[TreeNode], level: int, levels: List[int]) -> None:
        if not node:
            return

        if len(levels) == level:
            levels.append([])

        levels[level].append(node.val)
        self.helper(node.left, level + 1, levels)
        self.helper(node.right, level + 1, levels)

    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        levels = []
        self.helper(root, 0, levels)
        return levels

```

