# 移除元素


## Leetcode 27. 移除元素
给你一个数组 nums 和一个值 val，你需要 原地 移除所有数值等于 val 的元素，并返回移除后数组的新长度。

不要使用额外的数组空间，你必须仅使用 O(1) 额外空间并 原地 修改输入数组。

元素的顺序可以改变。你不需要考虑数组中超出新长度后面的元素。

<!--more-->

```python
# 双指针
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        slow = 0

        for fast in nums:
            if fast != val:
                nums[slow] = fast
                slow += 1
        
        return slow

# 双指针优化
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        left, right = 0, len(nums)

        while left < right:
            if nums[left] == val:
                nums[left] = nums[right - 1]
                right -= 1
            else:
                left += 1
        
        return left

```

```go
// 双指针
func removeElement(nums []int, val int) int {
    var(
        slow int = 0
    )

    for _, fast := range nums{
        if (fast != val) {
            nums[slow] = fast
            slow++
        } 
    }

    return slow
}

// 双指针优化
func removeElement(nums []int, val int) int {
    var(
        left int = 0
        right int = len(nums)   
    )

    for(left < right) {
        if nums[left] == val {
            nums[left] = nums[right - 1]
            right--
        }else{
            left++
        }
    }

    return left
}


```

