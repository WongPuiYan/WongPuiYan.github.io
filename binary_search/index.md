# 二分查找


# 二分查找
<!--more-->

```python
from typing import List


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

```golang
package main

import(
    "fmt"
)

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

