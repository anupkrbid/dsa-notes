# Swap two numbers

We use the XOR operator.
eg:
4 ^ 4 ^ 5 = 5
4 ^ 4 = 0
0 ^ 5 = 5

```py
def swap(a: int, b: int): # a = 7, b = 13
    a = a ^ b # a = 7 ^ 13 = 10
    b = a ^ b # b = 10 ^ 13 = 7
    a = a ^ b # a = 10 ^ 7 = 13
```
