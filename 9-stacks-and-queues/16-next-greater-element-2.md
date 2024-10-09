# Next Greater Element - 2

`[6,0,8,1,3]`

Given an array find the next greater element for each element in the array, if a greater element is not present to the right, we look for it from the seft start and still if it is not present we store -1 `[8.8,-1,3,6]`

## Solution 1

We can hypothetically assume that the length of the array is doubled and the elements are repeated. `[6,0,8,1,3]` become `[6,0,8,1,3, 6,0,8,1,3]` so here the 3 is in the 4<sup>th</sup> index which would normally have -1 as the nge but here we can keep searhing for ng2 to the right and find 6. so the orginal array ends at index 4 but to see beuong we can do `index % n` and can circle back to index 0.

### Code

```py
from typing import List

def next_greater_element_2(arr: List[int]) -> List[int]:
    L = len(arr)
    ans = [-1] * L # setting all index to -1

    for i in range(0, L, 1):
        for j in range(i+1, i + L-1, 1):
            virtual_index = j % L
            if arr[virtual_index] > arr[i]:
                ans[i] = (arr[virtual_index])
                break

    return ans
```

### Time & Space Complexity

**Time Complexity** -> _O(n<sup>2</sup>)_

**Space Complexity** -> _O(2n)_

## Solution 2

So we have already solved nge where we dont need to look for elements on the left. but now that we do, that means before we start comparing. W will do a pass through and pre full the stack witht he greatest elements, so that when we start cmparing the right most element,we already have data in the stack that tell us the greater element with respect to the first element in the array which is basically comparing from the left.

### Psudo Code

```py
from typing import List

def next_greater_element_2(arr: List[int]) -> List[int]:
    ans = []
    stack = Stack()
    L = len(arr)

    # this will prefill the stack with the initial set of grester elements
    for i in range(L-1, -1, -1):
        while not stack.is_empty() and stack.peek() <= arr[i]:
            stack.pop()
        stack.push(arr[i])

    for i in range(L-1, -1, -1):
        while not stack.is_empty() and stack.peek() <= arr[i]:
            stack.pop()

        if stack.is_empty():
            ans.append(-1)
        else:
            ans.append(stack.peek())

        stack.push(arr[i])

    return ans.reverse()
```

### Code

```py
from typing import List

def next_greater_element_2(arr: List[int]) -> List[int]:
    ans = []
    stack = []
    L = len(arr)

    for i in range(L-1, -1, -1):
        while len(stack) > 0 and stack[-1] <= arr[i]:
            stack.pop()
        stack.append(arr[i])

    for i in range(L-1, -1, -1):
        while len(stack) > 0 and stack[-1] <= arr[i]:
            stack.pop()

        if  len(stack) == 0:
            ans.append(-1)
        else:
            ans.append(stack[-1])

        stack.append(arr[i])

    return list(reversed(ans)) # ans[::-1]
```

### Time & Space Complexity

**Time Complexity** -> _O(4n)_

**Space Complexity** -> _O(2n)_
