# Clearing the i'th bit

If we can create a number where the i'th bit is not set and all the other bits are set and we do an AND with the actual number, this will work. Doing left shift for 1 times on 1 will set the i'th bit and then a NOT operation will flip all the bits.

```py
def clear_ith_bit(n: int, i: int):
    return n & ~(1 << i)
```
