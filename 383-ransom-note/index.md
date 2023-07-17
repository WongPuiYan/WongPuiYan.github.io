# 赎金信


## Leetcode 383. 赎金信
给你两个字符串：ransomNote 和 magazine ，判断 ransomNote 能不能由 magazine 里面的字符构成。
如果可以，返回 true ；否则返回 false 。
magazine 中的每个字符只能在 ransomNote 中使用一次。

<!--more-->

```python
# 列表  
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        ransom_count = [0] * 26
        magazine_count = [0] * 26

        for c in ransomNote:
            ransom_count[ord(c) - ord('a')] += 1
        for c in magazine:
            magazine_count[ord(c) - ord('a')] += 1

        return all(ransom_count[i] <= magazine_count[i] for i in range(26))

# 字典
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        counts = {}

        for c in magazine:
            counts[c] = counts.get(c, 0) + 1

        for c in ransomNote:
            if c not in counts or counts[c] == 0:
                return False
            counts[c] -= 1

        return True

# Counter
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        from collections import Counter
        return not Counter(ransomNote) - Counter(magazine)

# count
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        return all(ransomNote.count(c) <= magazine.count(c) for c in set(ransomNote))

```

