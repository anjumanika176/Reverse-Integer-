# Reverse-Integer-
LeetCode 7 Reverse Integer solution in Python 
# LeetCode 7: Reverse Integer

## Problem
Given a signed 32-bit integer `x`, return `x` with its digits reversed.
If reversing `x` causes the value to go outside the signed 32-bit integer range `[-2^31, 2^31 - 1]`, return `0`.

Assume the environment does not allow you to store 64-bit integers (signed or unsigned).

## Examples

| Input | Output | Explanation |
|-------|--------|-------------|
| `x = 123` | `321` | Digits reversed |
| `x = -123` | `-321` | The negative sign stays in front |
| `x = 120` | `21` | `021` becomes `21`, leading zero disappears |

## Constraints
- `-2^31 <= x <= 2^31 - 1`

## Approach
Take the last digit of the number, append it to the reversed number, and remove it from the original:

- `digit = x % 10` gives the last digit.
- `rev = rev * 10 + digit` appends the digit to the reversed number.
- `x = x // 10` removes the last digit.

Repeat until `x` becomes `0`.

### Python: handle the sign separately
In Python, `%` and `//` behave differently for negative numbers (`-123 // 10` is `-13`, not `-12`).
So the sign is saved first, the number is made positive, reversed, and the sign is applied at the end.
After that, if the result is outside `[-2^31, 2^31 - 1]`, `0` is returned.

### Edge cases

| Input | Output | Reason |
|-------|--------|--------|
| `120` | `21` | Trailing zero becomes a leading zero and disappears |
| `-123` | `-321` | Sign is kept |
| `0` | `0` | Loop does not run |
| `1534236469` | `0` | Reversed value `9646324351` is out of range |


```

## Complexity
- Time: O(log x), one loop step per digit
- Space: O(1)

## Concepts Used
- Modulo (`%`) and integer division (`//`)
- While loop
- Sign handling for negative numbers
- Integer overflow check

## Language
Python 3 

## Link
https://leetcode.com/problems/reverse-integer
