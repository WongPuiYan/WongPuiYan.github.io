# 三数之和


## leetcode 15. 三数之和
给你一个整数数组 nums ，判断是否存在三元组 [nums[i], nums[j], nums[k]] 满足 i != j、i != k 且 j != k ，同时还满足 nums[i] + nums[j] + nums[k] == 0 。请
你返回所有和为 0 且不重复的三元组。
注意：答案中不可以包含重复的三元组。

<!--more-->

```python
# 双指针
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        result = []
        nums.sort()
        n = len(nums)

        for i in range(n):
            if nums[0] > 0:
                break

            if i > 0 and nums[i] == nums[i - 1]:
                continue

            left = i + 1
            right = n - 1

            while left < right:
                tmp_sum = nums[i] + nums[left] + nums[right]

                if tmp_sum < 0:
                    left += 1
                elif tmp_sum > 0:
                    right -= 1
                else:
                    result.append([nums[i], nums[left], nums[right]])

                    while left < right and nums[left] == nums[left + 1]:
                        left += 1
    
                    while left < right and nums[right] == nums[right - 1]:
                        right -= 1
                    
                    left += 1
                    right -= 1

        return result

# 字典
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        result = []
        nums.sort()
        n = len(nums)

        for i in range(n):
            if nums[0] > 0:
                break

            if i > 0 and nums[i] == nums[i - 1]:
                continue

            tmp_dict = {}
            for j in range(i + 1, n):
                if i + 2 < j and nums[j] == nums[j - 1] == nums[j - 2]:
                    continue

                c = 0 - (nums[i] + nums[j])
                if c in tmp_dict:
                    result.append([nums[i], nums[j], c])
                    tmp_dict.pop(c)
                else:
                    tmp_dict[nums[j]] = j

        return result

```

