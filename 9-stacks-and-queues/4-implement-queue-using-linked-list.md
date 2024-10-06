# Implement Queue using Linked List

## Solution

```py
class Node:
    def __init__(self, data: int, next_node: "Node" = None):
        self.data = data
        self.next = next_node


class Queue:
    def __init__(self):
        self.count = 0
        self.front = None
        self.rear = None

    def push(self, val: int) -> None:
        temp = Node(val)

        if self.rear is not None:
            self.rear.next = temp

        if self.front is None:
            self.front = temp

        self.rear = temp
        self.count += 1

    def pop(self) -> int:
        if self.front is None:
            raise IndexError("Pop from Empty Queue")

        temp = self.front.data

        self.front = self.front.next
        self.count -= 1
        return temp

    def peek(self) -> int:
        if self.front is None:
            raise IndexError("Pop from Empty Queue")

        return self.front.data

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
from typing import TypeVar, Generic, Optional

# Define a type variable to represent any type
T = TypeVar('T')

# Generic Node class
class Node(Generic[T]):
    def __init__(self, data: T, next_node: Optional["Node[T]"] = None):
        self.data = data
        self.next = next_node

# Generic Queue class
class Queue(Generic[T]):
    def __init__(self):
        self.count = 0
        self.front: Optional[Node[T]] = None
        self.rear: Optional[Node[T]] = None

    def push(self, val: T) -> None:
        temp = Node(val)

        if self.rear is not None:
            self.rear.next = temp

        if self.front is None:
            self.front = temp

        self.rear = temp
        self.count += 1

    def pop(self) -> T:
        if self.front is None:
            raise IndexError("Pop from Empty Queue")

        temp = self.front.data

        self.front = self.front.next
        self.count -= 1
        return temp

    def peek(self) -> T:
        if self.front is None:
            raise IndexError("Pop from Empty Queue")

        return self.front.data

    def size(self) -> int:
        return self.count

    def is_empty(self) -> bool:
        return self.count == 0


# Queue of integers
int_queue = Queue[int]()
int_queue.push(10)
int_queue.push(20)
print(int_queue.pop())  # Output: 10
print(int_queue.peek())  # Output: 20


# Queue of strings
str_queue = Queue[str]()
str_queue.push("Mumbai")
str_queue.push("Delhi")
print(str_queue.pop())  # Output: "Mumbai"
print(str_queue.peek())  # Output: "Delhi"


# Queue of floats
float_queue = Queue[float]()
float_queue.push(3.14)
float_queue.push(2.718)
print(float_queue.pop())  # Output: 3.14
print(float_queue.peek())  # Output: 2.718

```
