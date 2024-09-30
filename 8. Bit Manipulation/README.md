# DSA Notes

## Bit Manipulation

### Decimal to Binary Convertion

(13)<sub>10</sub> -> (?)<sub>2</sub>

```sh
            ^ -----> (1101)
2 | 13 -> 1 |
-----       ^
2 | 6 -> 0  |
-----       ^
2 | 3 -> 1  |
-----       ^
  | 1       |
------------'

```

Start by dividing the no and writing the remainder on the right, continue this untill you reach 1 and then write from bottom to top and that will be your binary number, so (13)<sub>10</sub> -> (1101)<sub>2</sub>

```py
def convert_to_binary(n: int) -> str:
    res = ""
    while(n > 0):
        if (n%2 == 1):
            res+="1"
        else:
            res+="0"
        n = n//2

    res = res[::-1] # reversing a string
    return res
```

**Time Complexity** -> _O(log<sub>2</sub>(n))_

**Space Complexity** -> _O(log<sub>2</sub>(n))_

### Binary to Decimal Convertion

(1101)<sub>2</sub> -> (?)<sub>10</sub>

```sh
    1           1           0           1
 <----------<----------<-----------<---------<
 (1 * 2^3) + (1 * 2^2) + (0 * 2^1) + (1 * 2^0)

    8      +    4      +    0      +    1       ->  (13)
```

move from right to left with multiplying the (bit with (2 raised to the power of bit index)) and (add them), (1101)<sub>2</sub> -> (13)<sub>10</sub>

```py
def convert_to_decimal(n: str) -> int:
    length = len(n)
    sum = 0
    pow = 1
    for i in range(length - 1, -1, -1): # looping in decending order
        if rev_str[i] == "1":
            sum = sum + pow
        pow = pow * 2
    return sum
```

**Time Complexity** -> _O(log(n))_

**Space Complexity** -> _O(1)_

### 1<sup>s</sup> Complement & 2<sup>s</sup> Complement

#### 1<sup>s</sup> Complement

- flip the bits

#### 2<sup>s</sup> Complement

- flip the bits
- add 1 bit to it

```sh
1101  -->  0010 -> (0110 + 0001) ->  (0111)
            |            |              |
          (flip)      (add 1)           |
      (1s complemnt)            (2s complement)
```

#### How are negative numbers stored

The `int` stores 32 bits, as such (31, 30, 29 ..... 2, 1, 0), the 31<sup>st</sup> bit is used to determine if a no if negative or not. It the 31<sup>st</sup> bit is set (is 1) that means it is negative number af it is not set (is 0) then its not set.

**So how ia a negative number stored.**

For eg how is (-13) store

First it is stored as a positive number (31st bit is not set)

```sh
0 0.....1 1 0 1
- -     - - - -
^             ^
|             |
31st bit.     0th bit
```

then 2s complement is performed
first bits are flipped

```sh
1 1.....0 0 1 0
- -     - - - -
^             ^
|             |
31st bit.     0th bit
```

then 1 is added

```sh
1 1.....0 0 1 1
- -     - - - -
^             ^
|             |
31st bit.     0th bit
```

and this is how is a negative nnumber stored (31st bit will always be set)

**INT_MAX (2<sup>31</sup>-1)**

So what is the max positive number an `int` can store

The 31st bit will not be set and all other bits will be set

```sh
0 1.....1 1 1 1
- -     - - - -
^             ^
|             |
31st bit.     0th bit
```

So the total will be 2<sup>30</sup> + 2<sup>29</sup> + .... + 2<sup>1</sup> + 2<sup>0</sup> = **(2<sup>31</sup>-1)**

**INT_MIN (-2<sup>31</sup>)**

So what is the min negative number an `int` can store

```sh
1 0.....0 0 0 0
- -     - - - -
^             ^
|             |
31st bit.     0th bit
```

Then 2s complement is performed

_1<sup>st</sup>_ all bits are flipped

```sh
1 1.....0 0 1 0
- -     - - - -
^             ^
|             |
31st bit.     0th bit
```

then 1 is added

```sh
1 1.....0 0 1 1
- -     - - - -
^             ^
|             |
31st bit.     0th bit
```

and this is how is a negative nnumber stored (31st bit will always be set)

So the total will be **(-2<sup>31</sup>)**

### Operators (AND, OR, XOR, NOT, SHIFT)

#### AND

- all 1 -> 1
- one 0 -> 0

```sh
13 & 7 -> 9

  1 1 0 1  (13)
  0 1 1 1   (7)
& ------- (AND)
  0 1 0 1   (9)
```

#### OR

- all 0 -> 0
- one 1 -> 1

```sh
13 | 7 -> 15

  1 1 0 1 (13)
  0 1 1 1  (7)
| ------- (OR)
  1 1 1 1 (15)
```

#### XOR

- even no of 1 -> 0
- odd no of 1 -> 1

```sh
13 ^ 7 -> 10

  1 1 0 1  (13)
  0 1 1 1   (7)
^ ------- (XOR)
  1 0 1 0  (10)
```

#### Right Shift

- bits move to the right by a certain no
- the bit on the extreme right will go off
- x >> k = (x/2<sup>k</sup>)
  - 101 -> 1x2<sup>2</sup> + 0x2<sup>1</sup> + 1x2<sup>0</sup>
  - 010 -> 0x2<sup>2</sup> + 1x2<sup>1</sup> + 0x2<sup>0</sup>
  - so if we shift the bits to the right by 1 we just divide the decimal value by 2<sup>k</sup>, where k is 1,2,3 (no of shifts)

```sh
13 >> 1 -> 6
13 >> 2 -> 3

     1 1 0 1            (13)
>> 1 ------- (Right Shift 1)
     0 1 1 0             (6)


     1 1 0 1            (13)
>> 2 ------- (Right Shift 1)
     0 0 1 1             (3)
```

#### Left Shift

- bits move to the left by a certain no
- the bit on the extreme left will overflow and can give unexpected numbers
- (2<sup>31</sup>-1) << 1 -> will overflow and five wierd numbers, so one needs to be careful about it

```sh
13 << 1 -> 26
13 << 2 -> 52

     0 1 1 0 1           (13)
<< 1 --------- (Left Shift 1)
     1 1 0 1 0           (26)


     0 0 1 1 0 1           (13)
<< 2 ----------- (Left Shift 2)
     1 0 1 0 1 0           (52)
```

#### NOT

- 1s complement is performed (flip the bits)
- check if it's a negative number
  - if yes perform a 2's complement (flip the bits and add 1)
  - if no leave it at that

**~(NOT of a Positive Number)**

~(5) -> -6

```sh
0 0.....0 1 0 1    -> (5)
- -     - - - -
^             ^
|             |
31st bit.     0th bit
```

1s complement is performed

```sh
1 1.....1 0 1 0    -> (bits flipped)
- -     - - - -
^             ^
|             |
31st bit.     0th bit
```

Since it is a negative no 2s complement is performed

```sh
0 0.....0 1 0 1    -> (bits flipped)
             +1    -> (1 added)
- -     - - - -
0 0.....0 1 1 0    -> (-6)
- -     - - - -
^             ^
|             |
31st bit.     0th bit
```

**~(NOT of a Negative Number)**

~(-6) -> 5

First -6 will be stored as 2s compliemnt

```sh
0 0.....0 1 1 0    -> (6)
1 1.....1 0 0 1    -> (bits flipped)
            + 1    -> (add 1)
- -     - - - -
1 1.....1 0 1 0    -> (2s complement)
- -     - - - -
^             ^
|             |
31st bit.     0th bit
```

now NOT will be performed
1s complement is performed

```sh
1 1.....1 0 1 0
0 0.....0 1 0 1     -> (bits flipped)
- -     - - - -
^             ^
|             |
31st bit.     0th bit
```

Since it is a positive, this is the final value which is 5
