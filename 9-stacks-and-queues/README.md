# Stacks & Queues

These are the operations available in a stack and queue

- **push():** Insert the element in the stack
- **pop():** Remove and return the topmost element of the stack
- **peek():** Return the topmost element of the stack
- **size():** Return the number of remaining elements in the stack

**Stack is LIFO (Last In First Out)**

```sh
   [ , , , , , , , , ] <- (enqueue)
    ^               ^  -> (dequeuq)
    |               |
  front            rear

```

```py
stack = []
stack.append('1') # push
print(stack.pop()) # pop
print(stack[-1]) # peek
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
print(queue[0]) # peek
print(len(queue)) # size
```

## Problems

### Learning

[1. Implement Stack using Arrays](1-implement-stack-using-arrays.md)

[2. Implement Queue using Arrays](1-implement-queue-using-arrays.md)

[3. Implement Stack using Linked List](3-implement-stack-using-linked-list.md)

[4. Implement Queue using Linked List](4-implement-queue-using-linked-list.md)

[5. Implement Stack using Queue](5-implement-stack-using-queue.md)

[6. Implement Queue using Stack](6-implement-queue-using-stack.md)

[7. Balanced Parentheses](7-balanced-parentheses.md)

[8. Min Stack](8-min-stack.md)
