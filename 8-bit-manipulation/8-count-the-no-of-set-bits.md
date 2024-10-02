# Count the number of set bits

## Solution 1 - Brute

Just convert the decimal to binary and while conveting count the number of 1's

**Time Complexity** -> _O(log<sub>2</sub>(n))_

```py
def count_set_bits(n: int):
    count = 0
    while n != 0:
        if n % 2 == 1: # n & 1 == 1 (diff syntax to find if odd no)
            count+=1
        n = n // 2 # n = n >> 1 (diff syntax to divide by 2 )
    return count
```

## Solution 2 - Better

This `n & (n-1)` code will unset the right most set bit, and this will be done untill the number becomes 0, at which point all the set bits have been turned off

**Time Complexity** -> _O(no of set bits)_

```py
def count_set_bits(n: int):
    count = 0
    while n != 0:
        n = n & (n-1)
        count += 1
    return count
```
