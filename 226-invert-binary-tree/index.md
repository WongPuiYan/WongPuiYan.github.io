# 翻转二叉树


## 226. 翻转二叉树
给你一棵二叉树的根节点 root ，翻转这棵二叉树，并返回其根节点。

<!--more-->

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

# 递归 前序遍历
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if root is None:
            return None

        root.left, root.right = root.right, root.left
        self.invertTree(root.left)
        self.invertTree(root.right)

        return root

# 递归 中序遍历
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if root is None:
            return None

        self.invertTree(root.left)
        root.left, root.right = root.right, root.left
        self.invertTree(root.left)

        return root

# 递归 后序遍历
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if root is None:
            return None

        self.invertTree(root.left)
        self.invertTree(root.right)
        root.left, root.right = root.right, root.left

        return root

# 迭代 前序遍历
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if root is None:
            return None

        stack = [root]
        while stack:
            node = stack.pop()

            node.left, node.right = node.right, node.left

            if node.left:
                stack.append(node.left)

            if node.right:
                stack.append(node.right)

        return root

# 迭代 中序遍历
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if root is None:
            return None

        stack = [root]
        while stack:
            node = stack.pop()

            if node.left:
                stack.append(node.left)

            node.left, node.right = node.right, node.left

            if node.left:
                stack.append(node.left)

        return root

# 迭代 后序遍历
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if root is None:
            return None

        stack = [root]
        while stack:
            node = stack.pop()

            if node.left:
                stack.append(node.left)

            if node.right:
                stack.append(node.right)

            node.left, node.right = node.right, node.left

        return root

# 层序遍历 广度优先遍历
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if root is None:
            return None

        queue = collections.deque([root])
        while queue:
            for i in range(len(queue)):
                node = queue.popleft()

                node.left, node.right = node.right, node.left

                if node.left:
                    queue.append(node.left)

                if node.right:
                    queue.append(node.right)

        return root

```

