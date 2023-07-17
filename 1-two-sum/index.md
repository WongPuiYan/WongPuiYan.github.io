# 两数之和


## Leetcode 1. 两数之和
给定一个整数数组 nums 和一个整数目标值 target，请你在该数组中找出 和为目标值 target  的那 两个 整数，并返回它们的数组下标。
你可以假设每种输入只会对应一个答案。但是，数组中同一个元素在答案里不能重复出现。
你可以按任意顺序返回答案。

<!--more-->

```python
# 集合
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        records = set()

        for index, value in enumerate(nums):
            tmp = target - value
            if tmp in records:
                return [index, nums.index(tmp)]
            records.add(value)

# 字典
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        records = dict()

        for index, value in enumerate(nums):
            tmp = target - value
            if tmp in records:
                return [index, records[tmp]]
            records[value] = index

```

