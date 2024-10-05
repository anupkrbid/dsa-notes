# Stacks & Queues

These are the operations available in a stack and queue

- **push():** Insert the element in the stack
- **pop():** Remove and return the topmost element of the stack
- **top():** Return the topmost element of the stack
- **size():** Return the number of remaining elements in the stack

**Stack is LIFO (Last In First Out)**

```py
stack = []
stack.append('1') # push
print(stack.pop()) # pop
print(stack[-1]) # top
print(len(queue)) # size
```

**Queue is FIFO (First In First Out)**

```sh
(dequeue) <- [ , , , , , , , , ] <- (enqueue)
              ^               ^
              |               |
            front            rear

```

```py
queue = []
queue.append('1') # push
print(queue.pop(0)) # pop
print(queue[0]) # top
print(len(queue)) # size
```

## Problems

[1. Implement Stack using Arrays](1-implement-stack-using-arrays.md)

[2. Implement Queue using Arrays](1-implement-queue-using-arrays.md)
