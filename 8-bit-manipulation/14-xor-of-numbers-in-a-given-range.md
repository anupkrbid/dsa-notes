# XOR of Numbers in a Given Range

## Solution 1

Just loop thorugh the array and **XOR** each and every number to get the final result.

**Time Complexity** -> _O(n)_

**Space Complexity** -> _O(1)_

## Solution 2

We will do the XOR of different numbers we can see a pattern

```sh
N                                 XOR
1  -> 1                           = 1
2  -> 1^2                         = 3
3  -> 1^2^3                       = 0
4  -> 1^2^3^4                     = 4

5  -> 1^2^3^4^5                   = 1
6  -> 1^2^3^4^5^6                 = 7
7  -> 1^2^3^4^5^6^7               = 0
8  -> 1^2^3^4^5^6^7^8             = 8

9  -> 1^2^3^4^5^6^7^8^9           = 1
10 -> 1^2^3^4^5^6^7^8^9^10        = 11
11 -> 1^2^3^4^5^6^7^8^9^10^11     = 0
12 -> 1^2^3^4^5^6^7^8^9^10^11^12  = 12
```

If we look at this pattern we can see that if we group this in sets of 4 we can see that

N % 4 == 1 -> 1

N % 4 == 2 -> N+1

N % 4 == 3 -> 0

N % 4 == 0 -> N

```py
def xor_of_numbers_till(n: int):
    if n % 4 == 1:
        return 1
    if n % 4 == 2:
        return n + 1
    if n % 4 == 3:
        return 0
    if n % 4 == 4:
        return n
```

**Time Complexity** -> _O(1)_

**Space Complexity** -> _O(1)_

### Follow UP

What is **XOR** from **(x, y)**

So if we use the above funtion to generate `xor_of_numbers_till(x-1)` and `xor_of_numbers_till(y)` behind the scenes it will work like

```sh
xor_range(x, y) -> xor_range(4, 7)

xor_of_numbers_till(3) ^ xor_of_numbers_till(7)

1 ^ 2 ^ 3 ^
1 ^ 2 ^ 3 ^ 4 ^ 5 ^ 6 ^ 7
= 4 ^ 6 ^ 7
```

```py
def xor_of_numbers_in_range(x: int, y: int):
    return xor_of_numbers_till(x-1) ^ xor_of_numbers_till(y)
```

**Time Complexity** -> _O(1)_

**Space Complexity** -> _O(1)_
