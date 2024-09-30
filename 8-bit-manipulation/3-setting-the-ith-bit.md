# Setting the i'th bit

We can take the number 1 and left shift it `i` times so the set bit is the i'th bit and we perform an OR operator so the i'th bit gets set incase its not already and the other bits remain same.

```py
def set_ith_bit(n: int, i: int):
    return (n | (1 << i))
```
