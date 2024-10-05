# Implement Queue using Arrays

## Solution

```
class Queue:
    def __init__(self):
        self.front = -1
        self.rear = -1
        self.curr_size = 0
        self.max_size = 16
        self.arr = [0] * self.max_size


    def push(self, new_element: int) -> None:
        if self.curr_size == self.max_size:
            print("Queue is full\nExiting...")
            exit(1)

        if self.rear == -1:
            self.front = 0
            self.rear = 0
        else:
            self.rear = (self.rear + 1) % self.max_size # this stores data in a rotation pattern if there is space in the front and no space in the rear to enqueue data

        self.arr[self.rear] = new_element
        print("The element pushed is", new_element)
        self.curr_size += 1


    def pop(self) -> int:
        if self.front == -1:
            print("Queue Empty\nExiting...")

        popped = self.arr[self.front]

        if self.curr_size == 1:
            self.front = -1
            self.rear = -1
        else:
            self.front = (self.front + 1) % self.max_size

        self.curr_size -= 1
        return popped


    def top(self) -> int:
        if self.front == -1:
            print("Queue is Empty")
            exit(1)

        return self.arr[self.front]


    def size(self) -> int:
        return self.curr_size
```

### Time & Space Complexity

**Time Complexity - Pop Function** -> _O(1)_

**Time Complexity - Push Function** -> _O(1)_

**Time Complexity - Top Function** -> _O(1)_

**Time Complexity - Size Function** -> _O(1)_

**Space Complexity** -> _O(declared size of array)_
