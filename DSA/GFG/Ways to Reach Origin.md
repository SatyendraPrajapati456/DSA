# Ways to Reach Origin

## 1. Problem Details

**Platform:** GeeksforGeeks

**Question Link:**
https://www.geeksforgeeks.org/problems/paths-to-reach-origin3850/1

**Question Name:** Ways to Reach Origin

**Question Description:**

Refer to GeeksforGeeks problem statement.

## 2. Test Cases

### Test Case 1: Standard Case

Input:
```text
x=3, y=0
```

Output:
```text
1
```

Explanation:
Only one path exists: moving left three times.

### Test Case 2: Small Grid

Input:
```text
x=3, y=2
```

Output:
```text
10
```

Explanation:
This is equivalent to finding combinations C(3+2, 2) = 5! / (3!2!) = 10.

### Test Case 3: Origin

Input:
```text
x=0, y=0
```

Output:
```text
1
```

Explanation:
Already at the origin, one way (do nothing).

## 3. AI-Generated Approach

### Approach: Top-Down Dynamic Programming (Memoization)

The number of ways to reach (x, y) from (0, 0) is the sum of ways to reach (x-1, y) and (x, y-1), representing the two possible moves (left or down) to reach the current cell.

**Step-by-Step Reasoning:**
1. Initialize a 2D DP table of size (x+1) x (y+1) with -1 to represent uncomputed states.
2. Define a recursive function that returns 1 if x=0 and y=0 (base case).
3. For any state (x, y), recursively compute the sum of paths from (x-1, y) and (x, y-1) if the coordinates are within bounds.
4. Store the result in the DP table to avoid redundant calculations and return the value modulo 10^9 + 7.

**Why It Works:**
The problem exhibits optimal substructure and overlapping subproblems. Since each move reduces the distance to the origin, the recursion is guaranteed to terminate, and memoization ensures each state is computed only once.

### Time Complexity

O(x * y)

### Space Complexity

O(x * y)

## 4. Java Solution

### Required Concepts

- Memoization
- Recursion
- Integer Overflow Prevention

### Original Accepted Submission

```java
import java.util.*;

class Solution {
    static final int MOD = 1000000007;

    public int ways(int x, int y) {
        int[][] dp = new int[x + 1][y + 1];

        for (int[] row : dp) {
            Arrays.fill(row, -1);
        }

        return solver(x, y, dp);
    }

    public int solver(int x, int y, int[][] dp) {
        if (x == 0 && y == 0) {
            return 1;
        }

        if (dp[x][y] != -1) {
            return dp[x][y];
        }

        int left = 0;
        int down = 0;

        if (x > 0) {
            left = solver(x - 1, y, dp);
        }

        if (y > 0) {
            down = solver(x, y - 1, dp);
        }

        return dp[x][y] = (int)(((long)left + down) % MOD);
    }
}
```

### AI-Generated Java Alternative

```java
class Solution {
    static final int MOD = 1000000007;
    public int ways(int x, int y) {
        int[][] dp = new int[x + 1][y + 1];
        for (int[] row : dp) java.util.Arrays.fill(row, -1);
        return solve(x, y, dp);
    }
    private int solve(int x, int y, int[][] dp) {
        if (x == 0 && y == 0) return 1;
        if (dp[x][y] != -1) return dp[x][y];
        long res = 0;
        if (x > 0) res += solve(x - 1, y, dp);
        if (y > 0) res += solve(x, y - 1, dp);
        return dp[x][y] = (int)(res % MOD);
    }
}
```

## 5. Python Solution

### Required Concepts

- Memoization
- Recursion Depth
- List Comprehension

### AI-Generated Python Implementation

```python
class Solution:
    def ways(self, x: int, y: int) -> int:
        MOD = 1000000007
        memo = [[-1 for _ in range(y + 1)] for _ in range(x + 1)]
        def solve(i, j):
            if i == 0 and j == 0: return 1
            if memo[i][j] != -1: return memo[i][j]
            res = 0
            if i > 0: res += solve(i - 1, j)
            if j > 0: res += solve(i, j - 1)
            memo[i][j] = res % MOD
            return memo[i][j]
        return solve(x, y)
```

## 6. C++ Solution

### Required Concepts

- STL Vectors
- Recursion
- Memory Management

### AI-Generated C++ Implementation

```cpp
#include <vector>
class Solution {
    int MOD = 1000000007;
    int solve(int x, int y, std::vector<std::vector<int>>& dp) {
        if (x == 0 && y == 0) return 1;
        if (dp[x][y] != -1) return dp[x][y];
        long long res = 0;
        if (x > 0) res += solve(x - 1, y, dp);
        if (y > 0) res += solve(x, y - 1, dp);
        return dp[x][y] = (int)(res % MOD);
    }
public:
    int ways(int x, int y) {
        std::vector<std::vector<int>> dp(x + 1, std::vector<int>(y + 1, -1));
        return solve(x, y, dp);
    }
};
```

## 7. Rust Solution

### Required Concepts

- Ownership
- Borrowing
- Vectors

### AI-Generated Rust Implementation

```rust
impl Solution {
    pub fn ways(x: i32, y: i32) -> i32 {
        let mut dp = vec![vec![-1; (y + 1) as usize]; (x + 1) as usize];
        Self::solve(x, y, &mut dp)
    }
    fn solve(x: i32, y: i32, dp: &mut Vec<Vec<i32>>) -> i32 {
        if x == 0 && y == 0 { return 1; }
        if dp[x as usize][y as usize] != -1 { return dp[x as usize][y as usize]; }
        let mut res: i64 = 0;
        if x > 0 { res += Self::solve(x - 1, y, dp) as i64; }
        if y > 0 { res += Self::solve(x, y - 1, dp) as i64; }
        dp[x as usize][y as usize] = (res % 1000000007) as i32;
        dp[x as usize][y as usize]
    }
}
```

## 8. Motivation

> "Success is the sum of small efforts, repeated day in and day out."

<div align="center">

## Thank You 🚀

</div>
