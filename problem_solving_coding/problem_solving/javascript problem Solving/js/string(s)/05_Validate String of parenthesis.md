### Validate string of parentheses

```js
//Example Inputs:

validate('{}[]()');
// true

validate('{[()]}');
// true

validate('{[}]');
// false, they are not in the right order

validate('{}}');
// false, last `}` is not paired with `{`
```

```js
function validate(s) {
  const stack = [];
  const pairs = {
    ')': '(',
    ']': '[',
    '}': '{',
  };

  for (let char of s) {
    //first if condition gets satisfy if your traversing character matches with the keys only ex: },],)
    if (char in pairs) {
      // If the character is a closing parenthesis
      if (stack.pop() !== pairs[char]) {
        // The popped value from the stack should match the corresponding opening parenthesis (to get true)
        return false;
      }
    } else {
      stack.push(char);
    }
  }

  return stack.length === 0; // The stack should be empty for a valid string
}

console.log(validate('{}[]()')); // true
console.log(validate('{[()]}')); // true
console.log(validate('{[}]')); // false
console.log(validate('{}}')); // false
```
