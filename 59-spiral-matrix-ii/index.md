# 螺旋矩阵 II


# 螺旋矩阵 II

## 59. 螺旋矩阵 II
给你一个正整数 n ，生成一个包含 1 到 n2 所有元素，且元素按顺时针顺序螺旋排列的 n x n 正方形矩阵 matrix 。

<!--more-->

```python
class Solution:
    def generateMatrix(self, n: int) -> List[List[int]]:
        res = [[0] * n for _ in range(n)]
        x, y = 0, 0
        loop = mid = n // 2
        count = 1

        for i in range(1, loop + 1):
            # 从左到右
            for j in range(y, n - i):
                res[x][j] = count
                count += 1
            # 从上到下
            for j in range(x, n - i):
                res[j][n - i] = count
                count += 1
            # 从右到左
            for j in range(n - i, y, -1):
                res[n - i][j] = count
                count += 1
            # 从下到上
            for j in range(n - i, x, -1):
                res[j][y] = count
                count += 1
            x += 1
            y += 1

        if n % 2 != 0:
            res[mid][mid] = count
        return res

```
