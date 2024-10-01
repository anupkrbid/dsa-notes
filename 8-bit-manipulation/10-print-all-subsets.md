# Power Set/Printing all subsets

nums = [1,2,3]

result = [[], [1], [2], [3], [1,2], [1,3], [2,3], [1,2,3]]

N = 1 -> 2<sup>1</sup> = 2

N = 2 -> 2<sup>2</sup> = 4

N = 3 -> 2<sup>3</sup> = 8

_2<sup>n</sup> = `1 << n`_

```sh
     [1, 2, 3]
      ^  ^  ^
Dec   |  |  |  -> 0(dont take), 1(take)
1 -> [0, 0, 0] -> []
2 -> [0, 0, 1] -> [3]
3 -> [0, 1, 0] -> [2]
4 -> [0, 1, 1] -> [2,3]
5 -> [1, 0, 0] -> [1]
6 -> [1, 0, 1] -> [1,3]
7 -> [1, 1, 0] -> [1,2]
8 -> [1, 1, 1] -> [1,2,3]
```

So we loop from 0 -> (2<sup>n</sup>-1), find the binary value and select the elements from the array in the [set bit index](2-check-if-the-ith-bit-is-set-or-not.md), the binary representation of num determines which elements are included in the subset.

```py
def print_all_subsets(arr: List[int]):
    n = len(arr)
    subsets = 1 << n
    ans = []
    for num in range(subsets): # loops over each decimal value in subsets
        list = []
        for i in range(n): # loops over each bit in the array
            if (num & (1 << i)) > 0: # checks if the specific bit is set or not
                list.append(arr[i])
        ans.append(list)
    return ans
```
