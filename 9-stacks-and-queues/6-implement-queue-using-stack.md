# Implement Queue using Stack

## Solution 1

### Algorithm

- We will be using 2 stacks **S1** and **S2** to implement this
- when ever a **push()** operation is performed
  - first pop each item from **S1** and push to **S2** untill **S1** is empty
  - push new item in **S1**
  - then pop each item from **S2** and push to **S1** untill **S2** is empty
- then all the **pop()**, **peek()** and **size()** operations will happen on **S1**

### Psudo Code

```py
class Queue:
    def __init__(self):
        self.s1 = Stack()
        self.s2 = Stack()


    def push(self, val: int) -> None:
        while not self.s1.is_empty():
            temp = self.s1.pop()
            self.s2.push(temp)

        self.s1.push(val)

        while not self.s2.is_empty():
            temp = self.s2.pop()
            self.s1.push(temp)


    def pop(self) -> int:
        return self.s1.pop()


    def peek(self) -> int:
        return self.s1.peek()


    def size(self) -> int:
        return self.s1.size()
```

### Code

```py
class Queue:
    def __init__(self):
        self.s1 = []
        self.s2 = []


    def push(self, val: int) -> None:
        while len(self.s1) != 0:
            temp = self.s1.pop()
            self.s2.append(temp)

        self.s1.append(val)

        while len(self.s2) != 0:
            temp = self.s2.pop()
            self.s1.append(temp)


    def pop(self) -> int:
        if len(self.s1) == 0:
            raise IndexError("Pop from Empty Queue")
        return self.s1.pop()


    def peek(self) -> int:
        if len(self.s1) == 0:
            raise IndexError("Peek from Empty Queue")
        return self.s1[0]


    def size(self) -> int:
        return len(self.s1)
```

### Time & Space Complexity

**Time Complexity - Push Function** -> _O(2n)_

**Time Complexity - Pop Function** -> _O(1)_

**Time Complexity - Top Function** -> _O(1)_

**Time Complexity - Size Function** -> _O(1)_

**Space Complexity** -> _O(n)_

This approach has a high time complexity for push operations

## Solution 2 - Optimise push operations

### Algorithm

- We will be using 2 stacks **S1** and **S2** to implement this
- when ever a **push()** operation is performed
  - the item will be pushed to **S1**
- when ever a **pop()** or **peek()** operation is performed
  - we check if **S2** is not empty
    - we perform the **pop()** or **peek()** on **S2**
  - else
    - we pop each item from **S1** and push to **S2** untill **S1** is empty
    - we perform the **pop()** or **peek()** on **S2**
- for **size()** operation we perform a addition of the size of both **S1** and **S2**

### Psudo Code

```py
class Queue:
    def __init__(self):
        self.s1 = Stack()
        self.s2 = Stack()


    def push(self, val: int) -> None:
        self.s1.push(val)


    def pop(self) -> int:
        if not self.s2.is_empty():
            return self.s2.pop()
        else:
            while not self.s1.is_empty():
                temp = self.s1.pop()
                self.s2.push(temp)
            return self.s2.pop()


    def peek(self) -> int:
        if not self.s2.is_empty():
            return self.s2.peek()
        else:
            while not self.s1.is_empty():
                temp = self.s1.pop()
                self.s2.push(temp)
            return self.s2.peek()


    def size(self) -> int:
        return self.s1.size() + self.s2.size()
```

### Time & Space Complexity

**Time Complexity - Push Function** -> _O(1)_

**Time Complexity - Pop Function** -> _O(n)_

**Time Complexity - Top Function** -> _O(n)_

**Time Complexity - Size Function** -> _O(1)_

**Space Complexity** -> _O(n)_
