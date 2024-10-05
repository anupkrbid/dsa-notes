# Implement Stack using Arrays

These are the operations available in a stack

- push(): Insert the element in the stack
- pop(): Remove and return the topmost element of the stack
- top(): Return the topmost element of the stack
- size(): Return the number of remaining elements in the stack

## Solution

```
class Stack:
    def __init__(self):
        self.top = -1
        self.size = 1000
        self.arr = [0] * self.size


    def push(self, x: int) -> None:
        self.top += 1
        self.arr[self.top] = x


    def pop(self) -> int:
        x = self.arr[self.top]
        self.top -= 1
        return x


    def top(self) -> int:
        if self.top == -1:
            print("Stack is Empty")
            exit(1)

        return self.arr[self.top]


    def size(self) -> int:
        return self.top + 1

```

### Time & Space Complexity

**Time Complexity - Pop Function** -> _O(1)_

**Time Complexity - Push Function** -> _O(1)_

**Time Complexity - Top Function** -> _O(1)_

**Time Complexity - Size Function** -> _O(1)_

**Space Complexity** -> _O(declared size of array)_
