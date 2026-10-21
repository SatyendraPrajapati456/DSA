# Shortest Path From 1 To n

## 1. Problem Details

**Platform:** GeeksforGeeks

**Question Link:**
https://www.geeksforgeeks.org/problems/shortest-path-from-1-to-n0156/1

**Question Name:** Shortest Path From 1 To n

**Question Description:**

Refer to GeeksforGeeks problem statement.

## 2. Test Cases

### Test Case 1: Divisible by 3

Input:
```text
n = 9
```

Output:
```text
2
```

Explanation:
Starting at 9: 9 / 3 = 3 (step 1), 3 / 3 = 1 (step 2). Total steps = 2.

### Test Case 2: Mixed operations

Input:
```text
n = 4
```

Output:
```text
2
```

Explanation:
Starting at 4: 4 - 1 = 3 (step 1), 3 / 3 = 1 (step 2). Total steps = 2.

### Test Case 3: Base edge case

Input:
```text
n = 1
```

Output:
```text
0
```

Explanation:
Already at 1, so 0 steps are required.

## 3. AI-Generated Approach

### Approach: Reverse Greedy Approach

Instead of moving forward from 1 to n where branching decisions occur, move backward from n to 1. Dividing by 3 whenever possible reduces the value of n much faster than decrementing by 1.

**Step-by-Step Reasoning:**
1. Initialize a counter `steps` to 0.
2. Loop while `n > 1`.
3. Check if `n` is divisible by 3. If so, set `n = n / 3`.
4. Otherwise, decrement `n` by 1 (`n = n - 1`).
5. Increment `steps` after each operation.
6. Return `steps` once `n` reaches 1.

**Why It Works:**
In the forward direction, choosing between adding 1 or multiplying by 3 requires lookahead. However, moving backwards from n, if n is divisible by 3, division by 3 is strictly optimal because dividing reduces n by at least 2/3 of its value (for n >= 3, n - n/3 >= 2), which is always greater than or equal to subtracting 1. If n is not divisible by 3, the only valid reverse step from an integer state is decrementing by 1.

### Time Complexity

O(log3 n)

### Space Complexity

O(1)

## 4. Java Solution

### Required Concepts

- Greedy reduction
- Arithmetic operators
- Loop bounds

### Original Accepted Submission

```java
class Solution {
    public int minimumStep(int n) {
        int steps = 0;

        while (n > 1) {
            if (n % 3 == 0) {
                n /= 3;
            } else {
                n--;
            }
            steps++;
        }

        return steps;
    }
}
```

## 5. Python Solution

### Required Concepts

- Integer division //
- Greedy choice property
- Logarithmic steps

### AI-Generated Python Implementation

```python
class Solution:
    def minimumStep(self, n: int) -> int:
        steps = 0
        while n > 1:
            if n % 3 == 0:
                n //= 3
            else:
                n -= 1
            steps += 1
        return steps
```

## 6. C++ Solution

### Required Concepts

- Branching logic
- Integer division
- O(1) auxiliary space

### AI-Generated C++ Implementation

```cpp
class Solution {
public:
    int minimumStep(int n) {
        int steps = 0;

        while (n > 1) {
            if (n % 3 == 0) {
                n /= 3;
            } else {
                n--;
            }
            steps++;
        }

        return steps;
    }
};
```

## 7. Rust Solution

### Required Concepts

- Mutability with `mut`
- Integer arithmetic
- Idiomatic loop flow

### AI-Generated Rust Implementation

```rust
pub struct Solution;

impl Solution {
    pub fn minimum_step(mut n: i32) -> i32 {
        let mut steps = 0;

        while n > 1 {
            if n % 3 == 0 {
                n /= 3;
            } else {
                n -= 1;
            }
            steps += 1;
        }

        steps
    }
}
```

## 8. Motivation

> "When a problem looks complex moving forward, turn it upside down and work backward. Perspective often turns exponential branching into a single deterministic path."

<div align="center">

## Thank You 🚀

</div>
