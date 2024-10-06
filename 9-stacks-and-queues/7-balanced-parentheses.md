# Balanced Parentheses

Given a string `[]{()}` find if the parentheses are balanced or not

## Solution

### Algorithm

- We will use a stack here.
- when ever we find an oppening bracked we will push it into the stack
- when we find a closing bracked we will pop one item from the stack and match the opening bracked if they are same then we keep traversing the string
- once the string traversal is over and the stack is empty that means the parentheses are balanced or else they are not

### Psudo Code

```py
def balanced_parentheses(string: str) -> bool:
    stack = Stack()
    for ch in string:
        if ch == "(" or ch == "{" or ch == "[":
            stack.push(ch)
        else:
            if stack.is_empty():
                return False

            oppening_parantheses = stack.pop()

            if ch == ")" and oppening_parantheses != "(":
                return False

            if ch == "}" and oppening_parantheses != "{":
                return False

            if ch == "]" and oppening_parantheses != "[":
                return False

    return stack.is_empty()
```

### Code

```py
def balanced_parentheses(string: str) -> bool:
    stack = []
    for ch in string:
        if ch == "(" or ch == "{" or ch == "[":
            stack.append(ch)
        else:
            if len(stack) == 0:
                return False

            oppening_parantheses = stack.pop()

            if ch == ")" and oppening_parantheses != "(":
                return False

            if ch == "}" and oppening_parantheses != "{":
                return False

            if ch == "]" and oppening_parantheses != "[":
                return False

    return len(stack) == 0
```

### Time & Space Complexity

**Time Complexity** -> _O(n)_

**Space Complexity** -> _O(n)_
