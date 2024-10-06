# Implement Stack using Queue

## Solution

### Algorithms

- While pushing we have to reverse the items in the queue so that the pop() and peek() will return the last inserted item
- for that after er push the item in the queue we pop and push all the existing items int he queue

### Psudo Code

```py
class Stack:
    def __init__(self):
        self.q = Queue()

    def push(self, val: int) -> None:
        count = self.q.size()
        self.q.push(val)
        for i in range(count):
            popped_val = self.q.pop()
            self.q.push(popped_val)

    def pop(self) -> int:
        return self.q.pop()

    def peek(self) -> int:
        return self.q.peek()

    def size(self) -> int:
        return self.q.size()
```

### Code

```py
class Stack:
    def __init__(self):
        self.q = []

    def push(self, val: int) -> None:
        count = len(self.q)
        self.q.append(val)
        for i in range(count):
            popped_val = self.q.pop(0)
            self.q.append(popped_val)

    def pop(self) -> int:
        if len(self.q) == 0:
            raise IndexError("Pop from Empty Stack")
        return self.q.pop(0)

    def peek(self) -> int:
        if len(self.q) == 0:
            raise IndexError("Peek from Empty Stack")
        return self.q[0]

    def size(self) -> int:
        return len(self.q)
```

### Time & Space Complexity

**Time Complexity - Push Function** -> _O(n)_

**Time Complexity - Pop Function** -> _O(1)_

**Time Complexity - Top Function** -> _O(1)_

**Time Complexity - Size Function** -> _O(1)_

**Space Complexity** -> _O(n)_
