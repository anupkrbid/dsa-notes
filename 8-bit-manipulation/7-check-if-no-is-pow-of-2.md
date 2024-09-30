# Check if a number is a pow of 2

If a number is a power of 2 then it will always have only one set bit.

```sh
4 -> 1 0 0 (N)
3 -> 0 1 1 (N-1)
& (AND)
0 -> 0 0 0 (0)
```

```py
def check_if_no_is_pow_2(num: int):
    return (n & (n-1)) == 0
```
