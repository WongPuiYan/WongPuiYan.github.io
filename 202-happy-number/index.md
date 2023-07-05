# 快乐数


## 202. 快乐数
编写一个算法来判断一个数 n 是不是快乐数。

「快乐数」 定义为：

对于一个正整数，每一次将该数替换为它每个位置上的数字的平方和。
然后重复这个过程直到这个数变为 1，也可能是 无限循环 但始终变不到 1。
如果这个过程 结果为 1，那么这个数就是快乐数。
如果 n 是 快乐数 就返回 true ；不是，则返回 false 。

<!--more-->

```python
# 数组
class Solution:
    def isHappy(self, n: int) -> bool:
        def get_next(number):
            total_sum = 0
            while number > 0:
                number, digit = divmod(number, 10)
                total_sum += digit ** 2
            return total_sum

        exist = []
        while n != 1:
            n = get_next(n)
            if n in exist:
                return False
            exist.append(n)

        return True

# 集合
class Solution:
    def isHappy(self, n: int) -> bool:
        def get_next(number):
            total_sum = 0
            while number > 0:
                number, digit = divmod(number, 10)
                total_sum += digit ** 2
            return total_sum

        exist = set()
        while n != 1 and n not in exist:
            exist.add(n)
            n = get_next(n)

        return n == 1

# 快慢指针
class Solution:
    def isHappy(self, n: int) -> bool:
        def get_next(number):
            total_sum = 0
            while number > 0:
                number, digit = divmod(number, 10)
                total_sum += digit ** 2
            return total_sum

        slow = n
        fast = get_next(n)

        while fast != 1 and fast != slow:
            slow = get_next(slow)
            fast = get_next(get_next(fast))

        return fast == 1

```

