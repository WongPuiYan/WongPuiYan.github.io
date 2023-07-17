# 平衡二叉树


## Leetcode 110. 平衡二叉树
给定一个二叉树，判断它是否是高度平衡的二叉树。
本题中，一棵高度平衡二叉树定义为：
一个二叉树每个节点 的左右两个子树的高度差的绝对值不超过 1 。

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
    def get_height(self, root: TreeNode) -> int:
        if not root:
            return 0

        left = self.get_height(root.left)
        right = self.get_height(root.right)

        if left == -1 or right == -1 or abs(left - right) > 1:
            return -1

        return max(left, right) + 1

    def isBalanced(self, root: Optional[TreeNode]) -> bool:
        return self.get_height(root) != -1

class Solution:
    def isBalanced(self, root: Optional[TreeNode]) -> bool:
        if not root:
            return True

        height_map = {}
        stack = [root]

        while stack:
            node = stack.pop()

            if node:
                stack.append(node)
                stack.append(None)

                if node.left:
                    stack.append(node.left)
                if node.right:
                    stack.append(node.right)
            else:
                real_node = stack.pop()
                left = height_map.get(real_node.left, 0)
                right = height_map.get(real_node.right, 0)

                if abs(left - right) > 1:
                    return False

                height_map[real_node] = max(left, right) + 1

        return True

```

