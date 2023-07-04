# 有效的字母异位词


## 242. 有效的字母异位词
给定两个字符串 s 和 t ，编写一个函数来判断 t 是否是 s 的字母异位词。

注意：若 s 和 t 中每个字符出现的次数都相同，则称 s 和 t 互为字母异位词。

<!--more-->

```python
# 数组
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        record = [0] * 26
        
        for i in s:
            record[ord(i) - ord("a")] += 1
        
        for i in t:
            record[ord(i) - ord("a")] -= 1
        
        for i in record:
            if i != 0:
                return False
        
        return True

# 字典
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        s_dict = {}
        t_dict = {}

        for i in s:
            s_dict[i] = s_dict.get(i, 0) + 1
        
        for i in t:
            t_dict[i] = t_dict.get(i, 0) + 1
        
        return s_dict == t_dict

# 默认字典
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        from collections import defaultdict
        s_dict = defaultdict(int)
        t_dict = defaultdict(int)

        for i in s:
            s_dict[i] += 1

        for i in t:
            t_dict[i] += 1
        
        return s_dict == t_dict

# 计数器
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        from collections import Counter

        s_count = Counter(s)
        t_count = Counter(t)
    
        return s_count == t_count

```

