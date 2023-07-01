# 二分查找


## Leetcode 704. 二分查找
给定一个 n 个元素有序的（升序）整型数组 nums 和一个目标值 target  ，写一个函数搜索 nums 中的 target，如果目标值存在返回下标，否则返回 -1。

<!--more-->

```python
Class Solution:
    def search(sefl, nums: List[int], target: int) -> int:
        left, right = 0, len(nums) - 1

        while left <= right:
            mid = left + (right - left) // 2

            if target > nums[mid]:
                left = mid + 1
            elif target < nums[mid]:
                right = mid - 1
            else:
                return mid
        
        return -1

```

```go
func search(nums []int, target int) int {
    var(
        left int = 0
        right int = len(nums) - 1
        mid int
    )

    for left <= right {
        mid = left + (right - left) // 2

        if (num[mid] < target){
            left = mid + 1
        }else if (num[mid] > target){
            right = mid - 1
        }else{
            return mid
        }
    }

    return -1
}

```

