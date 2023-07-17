# 四数之和


## Leetcode 18. 四数之和
给你一个由 n 个整数组成的数组 nums ，和一个目标值 target 。请你找出并返回满足下述全部条件且不重复的四元组 [nums[a], nums[b], nums[c], nums[d]] （若两个四元组元素一一对应，则认为两个四元组重复）：

* 0 <= a, b, c, d < n
* a、b、c 和 d 互不相同
* nums[a] + nums[b] + nums[c] + nums[d] == target

你可以按 任意顺序 返回答案 。

<!--more-->

```python
# 双指针
class Solution:
    def fourSum(self, nums: List[int], target: int) -> List[List[int]]:
        nums.sort()
        n = len(nums)
        result = []

        for i in range(n):
            if nums[i] > target and nums[i] > 0 and target > 0:
                break

            if i > 0 and nums[i] == nums[i - 1]:
                continue

            for j in range(i + 1, n):
                if nums[i] + nums[j] > target and target > 0:
                    break

                if i + 1 < j and nums[j] == nums[j - 1]:
                    continue

                left = j + 1
                right = n - 1

                while left < right:
                    tmp_sum = nums[i] + nums[j] + nums[left] + nums[right]

                    if tmp_sum < target:
                        left += 1
                    elif tmp_sum > target:
                        right -= 1
                    else:
                        result.append([nums[i], nums[j], nums[left], nums[right]])

                        while left < right and nums[left] == nums[left + 1]:
                            left += 1

                        while left < right and nums[right] == nums[right - 1]:
                            right -= 1
                        
                        left += 1
                        right -= 1

        return result

# 字典
class Solution:
    def fourSum(self, nums: List[int], target: int) -> List[List[int]]:
        freq = {}
        res = set()
        n = len(nums)

        for num in nums:
            freq[num] = freq.get(num, 0) + 1

        for i in range(n):
            for j in range(i + 1, n):
                for k in range(j + 1, n):
                    val = target - (nums[i] + nums[j] + nums[k])
                    if val in freq:
                        count = (nums[i] == val) + (nums[j] == val) + (nums[k] == val)
                        if freq[val] > count:
                            res.add(tuple(sorted([nums[i], nums[j], nums[k], val])))

        return [list(i) for i in res]

```

