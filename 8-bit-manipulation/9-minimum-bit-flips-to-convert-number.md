# Minimum Bit Flips to Convert Number

So XOR is the only operator that can tell which bits are different, because even bits convert to 0 and and non even bits convet to 1, thenwe just have to [count the no of 1s/set bits](8-count-the-no-of-set-bits.md) in the result, that will tell use the no of flips needed

```py
def min_bit_flips_convert(num: int, target: int):
    res = num ^ target
    # return count_set_bits(res) # 8-count-the-no-of-set-bits
    count = 0

    while res != 0:
        res = res & (res - 1)
        count+=1

    return count
```
