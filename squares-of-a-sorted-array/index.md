# 有序数组的平方


# 有序数组的平方
## 977. 有序数组的平方
给你一个按 非递减顺序 排序的整数数组 nums，返回 每个数字的平方 组成的新数组，要求也按 非递减顺序 排序。

<!--more-->

```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        n = len(nums)
        res = [0] * n
        left, right, pos = 0, n - 1, n - 1

        while left <= right:
            if nums[left] ** 2 < nums[right] ** 2:
                res[pos] = nums[right] ** 2
                right -= 1
            else:
                res[pos] = nums[left] ** 2
                left += 1
            pos -= 1
        
        return res

```
