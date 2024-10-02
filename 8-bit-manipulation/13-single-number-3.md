# Single Number - 3

Given an array `[2,4,2,14,8,7,7,8]` where all number will appear twice except two distinct number which will appear only once, find those numbers.

## Solution 1

Hashing the numbers where key is the number value is the frequency and the fins the numers with frequency is 1

## Solution 2 - Concepts of Buckets

We we **XOR** all the nums in the array we will be left with **10** which is **14 ^ 4**, which means the set bits indexes in **10** denote that those indexes in **14** and **10** are different.

```sh
14 -> 1 1 1 0
 4 -> 0 1 0 0
 ^    XOR
10 -> 1 0 1 0
```

So we can take the rightmost set bit index and check each number in the array and check which number have a set bit in that index and based on that move them into two seperate buckets.

```sh
10 -> 1 0 1 0
 9 -> 1 0 0 1
 &    AND
 8 -> 1 0 0 0
10 -> 1 0 1 0
 ^ -> XOR
 2 -> 0 0 1 0
```

Based on this we can be sure that these two distinct numbers will be in different buckets allong with some similar numbers. Then if we XOR all the numbers in these buckets we will get the distinct numbers.

```sh
b1 (num with rightmost bit index set)
b2 (num with rightmost bit index not set)

num & 2 > 0 -> num with rightmost bit index set
```

```py
def single_number_3(arr: List[int]):
    xor = 0

    for num in arr:
        xor = xor ^ num
    right_most = (xor & (xor-1)) ^ xor

    b1 = 0
    b2 = 0

    for num in arr:
        if (num & right_most) > 0:
            b1 = b1 ^ num
        else:
            b2 = b2 ^ num
    return [b1, b2]
```

**Time Complexity** -> _O(2n)_

**Space Complexity** -> _O(1)_
