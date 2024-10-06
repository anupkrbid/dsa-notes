# Implement Stack using Linked List

## Solution

```py
class Node:
    def __init__(self, data: int, next_node: "Node" = None):
        self.data = data
        self.next = next_node


class Stack:
    def __init__(self):
        self.count = 0
        self.top = None

    def push(self, val: int) -> None:
        temp = Node(val)

        if self.top is not None:
            temp.next = self.top

        self.top = temp
        self.count += 1

    def pop(self) -> int:
        if self.top is None:
            raise IndexError("Pop from Empty Stack")

        temp = self.top.data
        self.top = self.top.next
        self.count -= 1
        return temp

    def peek(self) -> int:
        if self.top is None:
            raise IndexError("Top from Empty Stack")

        return self.top.data

    def size(self) -> int:
        return self.count

    def is_empty(self) -> bool:
        return self.count == 0
```

#### Time & Space Complexity

**Time Complexity - Push Function** -> _O(1)_

**Time Complexity - Pop Function** -> _O(1)_

**Time Complexity - Top Function** -> _O(1)_

**Time Complexity - Size Function** -> _O(1)_

**Space Complexity** -> _O(n)_

### Solution - Using Generic

```py
from typing import Generic, TypeVar, Optional

T = TypeVar('T')

class Node(Generic[T]):
    def __init__(self, data: T, next_node: Optional['Node[T]'] = None):
        self.data = data
        self.next = next_node

class Stack(Generic[T]):
    def __init__(self):
        self.count = 0
        self.top: Optional[Node[T]] = None

    def push(self, val: T) -> None:
        temp = Node(val)
        if self.top is not None:
            temp.next = self.top
        self.top = temp
        self.count += 1

    def pop(self) -> T:
        if self.top is None:
            raise IndexError("Pop from empty stack")
        temp = self.top.data
        self.top = self.top.next
        self.count -= 1
        return temp

    def peek(self) -> T:
        if self.top is None:
            raise IndexError("Top from empty stack")
        return self.top.data

    def size(self) -> int:
        return self.count

    def is_empty(self) -> bool:
        return self.count == 0


int_stack = Stack[int]()
int_stack.push(10)
int_stack.push(20)
print(int_stack.pop())  # Output: 20


string_stack = Stack[str]()
string_stack.push("India")
string_stack.push("Delhi")
print(string_stack.pop())  # Output: "Delhi"


float_stack = Stack[float]()
float_stack.push(3.14)
float_stack.push(1.618)
print(float_stack.pop())  # Output: 1.618
```
