# Next Greater Element - 1

`[6,0,8,1,3]`

Given an array find the next greater element for each element in the array, if a greater element is not present we store -1 `[8.8,-1,3,-1]`

## Solution 1 - Brute

Just iterate through the array and look for the next greater alement and push it into an **ans** array.

### Time & Space Complexity

**Time Complexity** -> _O(n<sup>2</sup>)_

**Space Complexity** -> _O(2n)_

## Solution 2 - Best

Since the greatest element will be on the right side, we can iterate from the right to the left and keep storing the greater element in an **ans** array and also push the current element in to a stack to keep track of the greater elements found till now. And if we come across an elemnt for which the top of the stack is not the greater element then we keep popping the stack till we find the greater element and then push the cureent elemenet and continue

### Psudo Code

```py
from typing import List

def next_greater_element(arr: List[int]) -> List[int]:
    ans = []
    stack = Stack()
    L = len(arr)

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

def next_greater_element(arr: List[int]) -> List[int]:
    ans = []
    stack = []
    L = len(arr)

    for i in range(L-1, -1, -1):
        while  len(stack) > 0 and stack[-1] <= arr[i]:
            stack.pop()

        if  len(stack) == 0:
            ans.append(-1)
        else:
            ans.append(stack[-1])

        stack.append(arr[i])

    return list(reversed(ans))  # ans[::-1]
```

### Time & Space Complexity

**Time Complexity** -> _O(2n)_

**Space Complexity** -> _O(2n)_
