# 两个数组的交集


## Leetcode 349. 两个数组的交集
给定两个数组 nums1 和 nums2 ，返回 它们的交集 。输出结果中的每个元素一定是 唯一 的。我们可以 不考虑输出结果的顺序 。

<!--more-->

```python
# 字典与集合
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        table = {}

        for num in nums1:
            table[num] = table.get(num, 0) + 1

        res = set()
        for num in nums2:
            if num in table:
                res.add(num)
                del table[num]
        
        return list(res)

# 数组
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        count1 = [0] * 1001
        count2 = [0] * 1001
        res = []

        for i in nums1:
            count1[i] += 1
        
        for i in nums2:
            count2[i] += 1
        
        for i in range(1001):
            if count1[i] * count2[i] > 0:
                res.append(i)
        
        return res

# 集合
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        return list(set(nums1) & set(nums2))

```

