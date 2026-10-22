# Diagonal Difference

## 1. Problem Details

**Platform:** HackerRank

**Question Link:**
https://www.hackerrank.com/challenges/diagonal-difference/problem

**Question Name:** Diagonal Difference

**Question Description:**

Given a square matrix, calculate the absolute difference between the sums of its diagonals.

For example, the square matrix $arr$ is shown below:

	1 2 3
    4 5 6
    9 8 9

- The left-to-right diagonal = $1 + 5 + 9 = 15$.
- The right-to-left diagonal = $3 + 5 + 9 = 17$.

Their absolute difference is $|15 - 17| = 2$.

**Function description**

Complete the $\textit{diagonalDifference}$ function with the following parameter:

-	$int\ arr[n][m]$: a 2-D array of integers

**Return**

-	$int$: the absolute difference in sums along the diagonals

Input Format:
The first line contains a single integer, $n$,  the number of rows and columns in the square matrix $arr$.
Each of the next $n$ lines describes a row, $arr[i]$, and consists of $n$ space-separated integers $arr[i][j]$.

Constraints:
+ $-100 \le arr[i][j] \le 100$

Output Format:

## 2. Test Cases

### Test Case 1: Standard 3x3 Matrix

Input:
```text
arr = [[11, 2, 4], [4, 5, 6], [10, 8, -12]]
```

Output:
```text
15
```

Explanation:
Primary diagonal is 11 + 5 + (-12) = 4. Secondary diagonal is 4 + 5 + 10 = 19. The absolute difference is |4 - 19| = 15.

### Test Case 2: Minimal 1x1 Matrix

Input:
```text
arr = [[5]]
```

Output:
```text
0
```

Explanation:
Primary diagonal is 5, secondary diagonal is 5. The absolute difference is |5 - 5| = 0.

### Test Case 3: 2x2 Matrix with Negative Numbers

Input:
```text
arr = [[-1, 1], [-1, -1]]
```

Output:
```text
2
```

Explanation:
Primary diagonal is (-1) + (-1) = -2. Secondary diagonal is 1 + (-1) = 0. The absolute difference is |-2 - 0| = 2.

## 3. AI-Generated Approach

### Approach: Single-Pass Matrix Traversal

For an n x n square matrix, both diagonal elements at any given row index i can be accessed directly using standard index relationships: the primary diagonal element is at (i, i) and the secondary diagonal element is at (i, n - 1 - i). We can accumulate both diagonal sums in a single pass of length n.

**Step-by-Step Reasoning:**
1. Determine the matrix dimension n from the number of rows.
2. Initialize two running sum accumulators, primary and secondary, to 0.
3. Iterate through index i from 0 up to n - 1.
4. Add arr[i][i] to primary and arr[i][n - 1 - i] to secondary.
5. Compute and return the absolute difference |primary - secondary|.

**Why It Works:**
In any square matrix of size n x n, the primary diagonal entries satisfy row == col (i.e., (i, i)), while the anti-diagonal entries satisfy row + col == n - 1 (i.e., (i, n - 1 - i)). Iterating through i from 0 to n - 1 visits every element of both diagonals exactly once without needing a nested O(n^2) loop.

### Time Complexity

O(n)

### Space Complexity

O(1)

## 4. Java Solution

### Required Concepts

- Nested List Indexing
- Math.abs
- Linear Traversal

### Original Accepted Submission

```java
import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.function.*;
import java.util.regex.*;
import java.util.stream.*;
import static java.util.stream.Collectors.joining;
import static java.util.stream.Collectors.toList;

class Result {

    /*
     * Complete the 'diagonalDifference' function below.
     *
     * The function is expected to return an INTEGER.
     * The function accepts 2D_INTEGER_ARRAY arr as parameter.
     */

    public static int diagonalDifference(List<List<Integer>> arr) {
    // Write your code here
        
        int n=arr.size();
        int primary = 0;
        int secondary = 0;

        for (int i = 0; i < n; i++) {
            primary += arr.get(i).get(i);
            secondary += arr.get(i).get(n - 1 - i);
        }

        return Math.abs(primary - secondary);
    }

}

public class Solution {
    public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.getenv("OUTPUT_PATH")));

        int n = Integer.parseInt(bufferedReader.readLine().trim());

        List<List<Integer>> arr = new ArrayList<>();

        IntStream.range(0, n).forEach(i -> {
            try {
                arr.add(
                    Stream.of(bufferedReader.readLine().replaceAll("\\s+$", "").split(" "))
                        .map(Integer::parseInt)
                        .collect(toList())
                );
            } catch (IOException ex) {
                throw new RuntimeException(ex);
            }
        });

        int result = Result.diagonalDifference(arr);

        bufferedWriter.write(String.valueOf(result));
        bufferedWriter.newLine();

        bufferedReader.close();
        bufferedWriter.close();
    }
}
```

### AI-Generated Java Alternative

```java
import java.util.List;

class Result {
    public static int diagonalDifference(List<List<Integer>> arr) {
        int n = arr.size();
        int primary = 0;
        int secondary = 0;

        for (int i = 0; i < n; i++) {
            primary += arr.get(i).get(i);
            secondary += arr.get(i).get(n - 1 - i);
        }

        return Math.abs(primary - secondary);
    }
}
```

## 5. Python Solution

### Required Concepts

- 2D List Indexing
- abs()
- Single Loop Optimization

### AI-Generated Python Implementation

```python
def diagonalDifference(arr: list[list[int]]) -> int:
    n = len(arr)
    primary = 0
    secondary = 0

    for i in range(n):
        primary += arr[i][i]
        secondary += arr[i][n - 1 - i]

    return abs(primary - secondary)
```

## 6. C++ Solution

### Required Concepts

- std::vector
- std::abs
- Direct Indexing

### AI-Generated C++ Implementation

```cpp
#include <vector>
#include <cmath>

int diagonalDifference(const std::vector<std::vector<int>>& arr) {
    int n = arr.size();
    int primary = 0;
    int secondary = 0;

    for (int i = 0; i < n; ++i) {
        primary += arr[i][i];
        secondary += arr[i][n - 1 - i];
    }

    return std::abs(primary - secondary);
}
```

## 7. Rust Solution

### Required Concepts

- Borrowing
- Indexing
- i32::abs

### AI-Generated Rust Implementation

```rust
pub fn diagonalDifference(arr: &[Vec<i32>]) -> i32 {
    let n = arr.len();
    let mut primary: i32 = 0;
    let mut secondary: i32 = 0;

    for i in 0..n {
        primary += arr[i][i];
        secondary += arr[i][n - 1 - i];
    }

    (primary - secondary).abs()
}
```

## 8. Motivation

> "Simplicity is prerequisite for reliability. Recognizing index symmetries turns quadratic scans into elegant linear walks."

<div align="center">

## Thank You 🚀

</div>
