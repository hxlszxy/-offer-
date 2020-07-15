# 30-包含min函数的栈

定义栈的数据结构，请在该类型中实现一个能够得到栈最小元素的min函数。在该栈中，调用min、push、pop的时间复杂度都是O(1)

## 题目分析

双栈

一个栈用来正常的push和pop，另一个栈用来存储当前的最小值。

push时，如果min栈为空则直接push，如果min不为空则和mintop比较，如果比mintop小则放在min栈中，如果大于min则对min再push一个mintop

pop时，直接pop，同时pop一个min栈的top元素，保持两个栈的元素个数是相同的。

查询min时，直接popmin栈的元素

## 代码实现

```python
class Solution:
    def __init__(self):
        self.stack = []
        self.minstack = []
    def push(self, node):
        self.stack.append(node)
        if self.minstack == [] or node < self.mine():
            self.minstack.append(node)
        else:
            self.minstack.append(self.mine())
    def pop(self):
		if self.stack == [] or self.minstack == []:
            return None
        self.stack.pop()
        self.minstack.pop()
    def top(self):
        return self.stack[-1]
    def mine(self):
        return self.minstack[-1]
```

