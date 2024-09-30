# Toggle the i'th bit

We can left shift 1 by i bits and perform a XOR with the actual number

```py
def toggle_ith_bit(n: int, i: int):
    return n ^ (1 << i)
```
