# Min Stack

These are the operations available in a min stack

- **push():** Insert the element in the stack
- **pop():** Remove and return the topmost element of the stack
- **peek():** Return the topmost element of the stack
- **size():** Return the number of remaining elements in the stack
- **getMin():** Return the min number in the stack (extra operation that is not available in the normal stack)

## Solution 1

### Algorithm

- for **push()** operation
  - add a tuple into the stack, where the first item in the tuple is the value and the second item in the tuple is the min value at that point
  - for the first stack item, the min value will be the initial value
  - fir subsequent push the current value will be compared with the last min value on top of the stack
- **pop()**, **peek()** and **size()** will be same as normal stack only the first item in the tuple will be returned

### Code

```py
from typing import Tuple
import sys

class Node:
    def __init__(self, data: Tuple[int, int], next_node=None):
        self.data = data
        self.next = next_node


class MinStack:
    def __init__(self):
        self.top = None
        self.count = 0

    def push(self, val: int) -> None:
        min_val = min(val, sys.maxsize if self.is_empty() else self.top.data[1])
        new_node = Node((val, min_val))

        if not self.is_empty():
            new_node.next = self.top

        self.top = new_node
        self.count += 1


    def pop(self) -> int:
        if self.is_empty():
            raise IndexError("pop() from Empty Stack")

        self.count -= 1
        temp = self.top
        self.top = self.top.next
        return temp.data[0]


    def peek(self) -> int:
        if self.is_empty():
            raise IndexError("peek() from Empty Stack")
        return self.top.data[0]


    def size(self) -> int:
        return self.count


    def is_empty(self) -> bool:
        return self.count == 0


    def get_min(self) -> int:
        if self.is_empty():
            raise IndexError("get_min() from Empty Stack")
        return self.top.data[1]
```

### Time & Space Complexity

**Time Complexity** -> _O(1)_

**Space Complexity** -> _O(2n)_

## Solution 2 - Best

### Algorithm

- the previous algo had a high space complexity which means we cannot use a tuple to store data here in the stack, instead we will use a single varibale to store the min
- for **push()** operation
  - if the value is more than **min** then we just puch it into the stack
  - if the value is less than **min** that means the **min** needs to be updated so we push **(2xval - prev_min)** into the stack and update the **min**
- for **pop()** operation
  - we check the **top** value if it is less than **min** that means the **top** was modified and the **min** also can to be modified after the pop, so we pop the value and midify **min** to **(2xcurrent_min - val)**
- for **peek()** operation
  - if **top** is less than the **_min_** then top value is returned or the min value is returned because if top is greater than min that means the top is a not modified or else the min is the top value
- for **get_min()** operation
  - we return the min value

### Code

```py
from typing import Tuple
import sys

class Node:
    def __init__(self, data: int, next_node=None):
        self.data = data
        self.next = next_node


class MinStack:
    def __init__(self):
        self.top = None
        self.min = sys.maxsize
        self.count = 0

    def push(self, val: int) -> None:

        if self.is_empty():
            self.top = Node(val)
            self.min = val
        else:
            if val < self.min:
                new_node = Node(2*val-self.min, self.top)
                self.top = new_node
                self.min = val
            else:
                new_node = Node(val, self.top)
                self.top = new_node

        self.count += 1


    def pop(self) -> int:
        if self.is_empty():
            raise IndexError("pop() from Empty Stack")

        self.count -= 1

        temp = self.top.data

        if temp < self.min:
            self.min = 2*self.min - temp
            self.top = self.top.next
        else:
             self.top = self.top.next

        return temp


    def peek(self) -> int:
        if self.is_empty():
            raise IndexError("peek() from Empty Stack")

        temp = self.top.data

        if temp > self.min:
            return temp

        return self.min


    def size(self) -> int:
        return self.count


    def is_empty(self) -> bool:
        return self.count == 0


    def get_min(self) -> int:
        if self.is_empty():
            raise IndexError("get_min() from Empty Stack")
        return self.min

```

### Time & Space Complexity

**Time Complexity** -> _O(1)_

**Space Complexity** -> _O(n)_
