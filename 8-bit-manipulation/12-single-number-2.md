# Single Number - 2

Given an array `[3,5,6,3,6,3,6]` where all number will appear thrice except one which will appear only once, find that number.

## Solution 1

| Decimal | Binary |
| :-----: | :----: |
|    3    |  0011  |
|    3    |  0011  |
|    3    |  0011  |
|    5    |  0101  |
|    6    |  0110  |
|    6    |  0110  |
|    6    |  0110  |

So if we arrange these numbers in order we can see that each bit the set bits for the duplicate numbers will always be in multiple of 3, for example fo 3 the 0<sup>th</sup> & 1<sup>st</sup> set bit are in multiple of 3, so that means if we [check each bit index for set bits](2-check-if-the-ith-bit-is-set-or-not.md) and count it along the way, we will find that if any index has an extra bit which is more than the multiple of 3 that means that [bit index should be set](3-setting-the-ith-bit.md) as there is a number which is not repeating.

```py
def single_number_2(arr: List[int]):
    ans = 0
    for bit in range(32):
        count = 0
        for num in arr:
            if num & (1 << bit) > 0:
                count += 1
        if count % 3 == 1:
            ans = ans | (1 << bit)
    return ans
```

<!-- **Time Complexity** -> _O(log<sub>2</sub>(n))_ -->

**Time Complexity** -> _O(32n)_

**Space Complexity** -> _O(1)_

## Solution 2

[3,3,3,5,6,6,6]

If we sort this array and start from 1<sup>st</sup> index, we can see that the previous index and current index values are same, which means we have not found the unique number yet, then we move three positions to the right and check again, incase both index are same we move again and try again, but it we find that the values dont match then we have found our answer and it is the index to the left. In case we donot finf the unique number and the loop ends that means it is the last item in the array.

```py
def single_number_2(arr: List[int]):
    arr.sort()
    for i in range(1, len(arr), 3):
        if arr[i] != arr[i-1]:
            return arr[i-1]
    return arr[-1]
```

**Time Complexity** -> _O(nlog(n) + n/3)_

**Space Complexity** -> _O(1)_

## Solution 3 - Cocept of Buckets

We will take three buckets to store numbers

`ones` -> to store all numbers occuring twice

`twos` -> to store all numbers occuring thrice

`threes` -> to store all numbers occuring thrice

When the way this works is we loop throught he array and we try to figure out where the number should be placed.

- if number is not in `twos`, it should go to `ones`, than we do an `ADD` operation on `ones`
- if number is in `ones` then it should go to `twos`, then we do an `ADD` operation on `twos` and `DELETE` operation on `ones`
- if number is in `twos`, then it should go to `threes`, then we do an `ADD` operation on `threes` and `DELETE` operation on `twos`

We dont really need to use `threes`, but this is only for better understanding.

```py
def single_number_2(arr: List[int]):
    ones = 0
    twos = 0
    for num in arr:
        ones = (ones ^ num) & ~twos
        two = (twos ^ num) & ~ones
    return ones
```

**Time Complexity** -> _O(n)_

**Space Complexity** -> _O(1)_
