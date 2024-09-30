# Removing the last rightmost set bit

For n = 12 => 1 1 0 0, we have to covert the right most 1 to 0, we can do this by performing an AND operation of the actual number and and 1 less than that number.

```sh
12 -> 1 1 0 0
11 -> 1 0 1 1
& (AND)
8  -> 1 0 0 0
```

```py
def remove_last_set_bit(n: int):
    return n & (n-1)
```
