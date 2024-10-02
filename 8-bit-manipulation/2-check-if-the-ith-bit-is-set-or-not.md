# Check if the i'th bit is set or not

We can use the left or the right shift operator to figure this out.

## Solution 1 - Left Shift

We can left shift the number 1 by i times, it will bring the set bit to the i'th bit and when we do an AND with the actual number all the bit are unset and resultant value will be number greater than zero if the i'th bit is set in n.

```py
def check_ith_bit_set_or_not(n: int, i: int):
    return (n & (1 << i)) > 0
```

## Solution 2 - Right Shift

We can right shift the number n by i times, it will bring the i'th bit to the 0'th bit and when we do an AND with the number 1, all the bit are unset and resultant value will be number greater than zero if the 0'th bit is set in n.

```py
def check_ith_bit_set_or_not(n: int, i: int):
    return ((n >> i) & 1) > 0
```
