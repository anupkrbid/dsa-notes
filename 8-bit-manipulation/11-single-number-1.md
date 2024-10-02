# Single Number - I

Given an array `[3,5,6,3,6]` where all number will apppear twice except one, find that number.

We can XOR all the numbers because XOR of two same number is zero and XOR of any number with zero is that number. So all the repeated numbers will become zero and only the unique number will be left out.

```py
def single_number(arr: List[int]):
    ans = 0
    for i in arr:
        ans = ans ^ i
    return ans
```
