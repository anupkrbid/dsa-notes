# Infix to Postfix Conversion

## Algorithm

- Start with an empty **stack S** and and empty **string ans**
- Iterate over the characters in the expression
- found an operand
  - add it to the **ans**
- found an operator
  - if stack is empty, put it in the stack
  - if stack is not empty and the top most operator has a lower priority then it will be pushed to the stack
  - if stack is not empty and the top most operator has a higher priority then it wll be popped and added it the ans till a lower priority operator is found on teh stack, at which point it will be added to the stack
  - if the found operator is a `(` just push it into the stack
  - if the found operator is a `)` just pop things from stack and add it to ans till you find a `)`
- once iteration is over all the remaining items from the stack is popped and added to ans

**Infix Expression** -> `a+b*(c^d-e)`

|        i=0         | stack    | ans        |
| :----------------: | :------- | :--------- |
|         a          | a        |            |
|         +          | +        | a          |
|         b          | +        | ab         |
|         \*         | +,\*     | ab         |
|         (          | +,\*,(   | ab         |
|         c          | +,\*,(   | abc        |
|         ^          | +,\*,(,^ | abc        |
|         d          | +,\*,(,^ | abcd       |
|         -          | +,\*,(,- | abcd^      |
|         e          | +,\*,(,- | abcd^e     |
|         )          | +,\*     | abcd^e-    |
|                    |          |            |
| Postfix Expression | ->       | abcd^e-\*+ |

## Psudo Code

```py
def infix_to_postfix(exp: str):
	stack = Stack()
	ans = ""

  	for ch in exp:
    	if is_operand(ch):
			ans = ans + ch
		elif ch == "(":
			stack.push(ch)
		elif ch == ")":
			while not stack.is_empty() and stack.peek() != "(":
				ans =+ stack.pop()
		else:
			while not stack.is_empty() and get_priority(stack.peek()) > get_priority(ch):
				ans += stack.pop()
			stack.push(ch)

	while not stack.is_empty():
		ans += stack.pop()

	return ans


def get_priority(operator):
  	if operator == "^":
		return 3

	if operator == "*" or operator == "/":
		return 2

	if operator == "+" or operator == "-":
		return 1

	return -1

def is_operand(ch: string):
  	return (ch >= "A" and ch <= "Z") or  (ch >= "a" and ch <= "z") or (ch >= "0" and ch <= "9")
```

### Time & Space Complexity

**Time Complexity** -> _O(n)_

**Space Complexity** -> _O(n)_
