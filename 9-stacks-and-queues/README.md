# Stacks & Queues

These are the operations available in a stack and queue

- **push():** Insert the element in the stack
- **pop():** Remove and return the topmost element of the stack
- **peek():** Return the topmost element of the stack
- **size():** Return the number of remaining elements in the stack

## Stack is LIFO (Last In First Out)\*\*

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

## Queue is FIFO (First In First Out)\*\*

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

## Prefix, Infix and Postfix

|  Prefix   |     Infix      |  Postfix  |
| :-------: | :------------: | :-------: |
| `*+pq-mn` | `(p+q)\*(m-n)` | `pq+mn-*` |

**Prefix**

Operators come before and are used extensively in aprogramming language called LISP and also used in Tree Data Structures.

**Infix**

Operators come in between and are something most prigramming languages understand like c, c++, etc.

**Postfix**

Operators come after and are used in stack based calculators.

**Operator**

^, \*, /, +, -

**Operand**

A-Z, a-z, 0-9

**Priority**

```sh
      ^         (3)
    *   /       (2)
    +   -       (1)
anything else  (-1)
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

### Prefix Infix Postfix Conversion

[9. Infix to Postfix Conversion](9-infix-to-postfix.md)

[10. Infix to Prefix Conversion](10-infix-to-prefix.md)

[11. Postfix to Infix Conversion](11-postfix-to-infix.md)

[12. Prefix to Infix Conversion](12-prefix-to-infix.md)

[13. Prefix to Postfix Conversion](13-prefix-to-postfix.md)

[14. Postfix to Prefix Conversion](14-postfix-to-prefix.md)

### Monotonic Stack and Queues
