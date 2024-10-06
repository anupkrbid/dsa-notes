# Implement Stack using Arrays

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


    def peek(self) -> int:
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
