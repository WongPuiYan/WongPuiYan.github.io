# 滑动窗口最大值


## Leetcode 239. 滑动窗口最大值
给你一个整数数组 nums，有一个大小为 k 的滑动窗口从数组的最左侧移动到数组的最右侧。你只可以看到在滑动窗口内的 k 个数字。滑动窗口每次只向右移动一位。
返回 滑动窗口中的最大值 。

<!--more-->

```python
class Solution:
    def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:
        que = collections.deque()

        for i in range(k):
            while que and nums[i] >= nums[que[-1]]:
                que.pop()
            que.append(i)

        res = [nums[que[0]]]
        for i in range(k, len(nums)):
            while que and nums[i] >= nums[que[-1]]:
                que.pop()
            que.append(i)

            while que[0] <= i - k:
                que.popleft()

            res.append(nums[que[0]])

        return res

```

