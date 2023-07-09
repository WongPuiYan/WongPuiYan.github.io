# 用队列实现栈


## 225. 
请你仅使用两个队列实现一个后入先出（LIFO）的栈，并支持普通栈的全部四种操作（push、top、pop 和 empty）。

实现 MyStack 类：
* void push(int x) 将元素 x 压入栈顶。
* int pop() 移除并返回栈顶元素。
* int top() 返回栈顶元素。
* boolean empty() 如果栈是空的，返回 true ；否则，返回 false 。

注意：
* 你只能使用队列的基本操作 —— 也就是 push to back、peek/pop from front、size 和 is empty 这些操作。
* 你所使用的语言也许不支持队列。 你可以使用 list （列表）或者 deque（双端队列）来模拟一个队列 , 只要是标准的队列操作即可。

<!--more-->

```python
class MyStack:

    def __init__(self):
        from collections import deque
        self.que = deque()

    def push(self, x: int) -> None:
        self.que.append(x)

    def pop(self) -> int:
        if self.empty():
            return None

        for i in range(len(self.que) - 1):
            self.que.append(self.que.popleft())

        return self.que.popleft()

    def top(self) -> int:
        if self.empty():
            return None
        else:
            return self.que[-1]

    def empty(self) -> bool:
        return not self.que


# Your MyStack object will be instantiated and called as such:
# obj = MyStack()
# obj.push(x)
# param_2 = obj.pop()
# param_3 = obj.top()
# param_4 = obj.empty()

```

