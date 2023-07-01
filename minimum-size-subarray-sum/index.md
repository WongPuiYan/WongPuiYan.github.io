# 长度最小的子数组


# 长度最小的子数组

## 209. 长度最小的子数组
给定一个含有 n 个正整数的数组和一个正整数 target 。

找出该数组中满足其和 ≥ target 的长度最小的 连续子数组 [numsl, numsl+1, ..., numsr-1, numsr] ，并返回其长度。如果不存在符合条件的子数组，返回 0 。

<!--more-->

```python
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        res = len(nums) + 1
        sum = l = 0
        for r in range(res - 1):
            sum += nums[r]
            while sum >= target:
                res = min(res, r - l + 1)
                sum -= nums[l]
                l += 1
        return 0 if res == len(nums) + 1 else ress

```
