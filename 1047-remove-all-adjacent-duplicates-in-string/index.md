# 1047 Remove All Adjacent Duplicates in String


## 1047. 删除字符串中的所有相邻重复项
给出由小写字母组成的字符串 S，重复项删除操作会选择两个相邻且相同的字母，并删除它们。
在 S 上反复执行重复项删除操作，直到无法继续删除。
在完成所有重复项删除操作后返回最终的字符串。答案保证唯一。

<!--more-->

```python
# 栈
class Solution:
    def removeDuplicates(self, s: str) -> str:
        res = list()

        for item in s:
            if res and res[-1] == item:
                res.pop()
            else:
                res.append(item)

        return "".join(res)

# 双指针
class Solution:
    def removeDuplicates(self, s: str) -> str:
        res = list(s)
        slow = 0
        fast = 0
        n = len(res)

        while fast < n:
            res[slow] = res[fast]

            if slow > 0 and res[slow] == res[slow - 1]:
                slow -= 1
            else:
                slow += 1
            
            fast += 1

        return ''.join(res[:slow])

```

