# Divide Two Integers without using Multiplication and Division Operators

So let say the number is N and the divisor is D. We have to think in terms of 2<sup>x</sup>. So for N = 22 and D = 3

22 -> 3 x 2<sup>0</sup> = 3

3 x 2<sup>1</sup> = 6

3 x 2<sup>2</sup> = 12

3 x 2<sup>3</sup> = 48

So the maximum no that can be removed from 14 is 12 and the max pow 2 was raised to here was 2

22 - 12 = 10 -> 3 x 2<sup>0</sup> = 3

3 x 2<sup>1</sup> = 6

3 x 2<sup>2</sup> = 12

So the maximum no that can be removed from 10 is 6 and the max pow 2 was raised to here was 1

20 - 6 = 4 -> 3 x 2<sup>0</sup> = 3

3 x 2<sup>1</sup> = 6

So the maximum no that can be removed from 4 is 3 and the max pow 2 was raised to here was 0

So to total value that was removed from 22 was (2<sup>2</sup> + 2<sup>1</sup> + 2<sup>0</sup>) = 7

So that is the answer

We have to take into consideration that the answer will be positive or negative. A negative answer is poiible incase the number or divisor any one is negative

```py
def divide_2_number(n: int, d: int):

    if n == d:
        return 1

    sign = True # positive
    if n >= 0 and d < 0:
        sign = False

    if n < 0 and d > 0:
        sign = False

    n = abs(n) # converting to positive no
    d = abs(d) # converting to positive no
    ans  = 0
    while n > d:
        count = 0
        while n >= (d << (count+1)): # n greater equal to d x 2 pow(count+1)
            count= count + 1

        n = n - (d << count)
        ans = ans + (1 << count)

    if ans >= (1 << 31) and not sign: # handling edge case where ans can go beyond max int value
        return (1 << 31) - 1

    if sign:
        return ans

    return (-1 * ans)
```
