# 找出字符串中第一个匹配项的下标


## Leetcode 28. 找出字符串中第一个匹配项的下标
给你两个字符串 haystack 和 needle ，请你在 haystack 字符串中找出 needle 字符串的第一个匹配项的下标（下标从 0 开始）。如果 needle 不是 haystack 的一部分，则返回  -1 。

<!--more-->

```python
# 前缀表（减一）
class Solution:
    def getNext(self, next: List[int], s: str) -> None:
        j = -1
        next[0] = j

        for i in range(1, len(s)):
            while j >= 0 and s[i] != s[j+1]:
                j = next[j]
            if s[i] == s[j+1]:
                j += 1
            next[i] = j

    def strStr(self, haystack: str, needle: str) -> int:
        if not needle:
            return 0
        next = [0] * len(needle)
        self.getNext(next, needle)
        j = -1

        for i in range(len(haystack)):
            while j >= 0 and haystack[i] != needle[j+1]:
                j = next[j]
            if haystack[i] == needle[j+1]:
                j += 1
            if j == len(needle) - 1:
                return i - len(needle) + 1
        return -1

# 前缀表（不减一）
class Solution:
    def getNext(self, next: List[int], s: str) -> None:
        j = 0
        next[0] = 0

        for i in range(1, len(s)):
            while j > 0 and s[i] != s[j]:
                j = next[j - 1]
            if s[i] == s[j]:
                j += 1
            next[i] = j
    
    def strStr(self, haystack: str, needle: str) -> int:
        if len(needle) == 0:
            return 0
        next = [0] * len(needle)
        self.getNext(next, needle)
        j = 0

        for i in range(len(haystack)):
            while j > 0 and haystack[i] != needle[j]:
                j = next[j - 1]
            if haystack[i] == needle[j]:
                j += 1
            if j == len(needle):
                return i - len(needle) + 1
        return -1

# 暴力法
class Solution(object):
    def strStr(self, haystack: str, needle: str) -> int:
        m, n = len(haystack), len(needle)

        for i in range(m):
            if haystack[i:i+n] == needle:
                return i
        return -1

# 使用index
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        try:
            return haystack.index(needle)
        except ValueError:
            return -1

# 使用index
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        return haystack.find(needle)

```

