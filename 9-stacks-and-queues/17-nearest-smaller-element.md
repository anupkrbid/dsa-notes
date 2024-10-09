# Previous Smaller Element

`[4,5,2,10,8]`

Given an array find the previos smaller element for each element in the array, if a smaller element is not present we store -1 `[-1,4,-1,2,2]`

## Solution 1 - Brute

Just iterate through the array and look for the previous greater alement and push it into an **ans** array.

### Time & Space Complexity

**Time Complexity** -> _O(n<sup>2</sup>)_

**Space Complexity** -> _O(2n)_

## Solution 2 - Best

Since the smaller element will be on the left side, we can iterate from the left to the right and keep storing the smalller element in an **ans** array and also push the current element in to a stack to keep track of the smaller elements found till now. And if we come across an elemnt for which the top of the stack is not the smaller element then we keep popping the stack till we find the smaller element and then push the cureent elemenet and continue

### Psudo Code

```py
from typing import List

def prev_smaller_element(arr: List[int]) -> List[int]:
    ans = []
    stack = Stack()

    for num in arr:
        while not stack.is_empty() and stack.peek() >= num:
            stack.pop()

        if stack.is_empty():
            ans.append(-1)
        else:
            ans.append(stack.peek())

        stack.push(num)

    return ans
```

### Code

```py
from typing import List

def prev_smaller_element(arr: List[int]) -> List[int]:
    ans = []
    stack = []
    L = len(arr)

    for num in arr:
        while  len(stack) > 0 and stack[-1] >= num:
            stack.pop()

        if  len(stack) == 0:
            ans.append(-1)
        else:
            ans.append(stack[-1])

        stack.append(num)

    return ans
```

### Time & Space Complexity

**Time Complexity** -> _O(2n)_

**Space Complexity** -> _O(2n)_
