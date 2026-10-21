# Status

## 1. Problem Details

**Platform:** Codeforces

**Question Link:**
https://codeforces.com/problemset/status

**Question Name:** Status

**Question Description:**

Refer to Codeforces problem statement.

## 2. Test Cases

### Test Case 1: Standard Status Stream

Input:
```text
n = 5, k = 1, statuses = [1, 0, 1, 1, 0]
```

Output:
```text
4
```

Explanation:
By flipping at most one invalid status (0) to valid (1), the longest contiguous valid status subsegment is from index 0 to 3 of length 4.

### Test Case 2: All Invalid Statuses

Input:
```text
n = 4, k = 1, statuses = [0, 0, 0, 0]
```

Output:
```text
1
```

Explanation:
With k = 1 tolerance, only a single 0 can be converted, yielding a maximum segment of length 1.

### Test Case 3: All Valid Statuses

Input:
```text
n = 3, k = 0, statuses = [1, 1, 1]
```

Output:
```text
3
```

Explanation:
All elements already possess valid status, so the entire array of length 3 is valid.

## 3. AI-Generated Approach

### Approach: Two Pointers / Sliding Window

Maintain a dynamic window representing contiguous valid status sequences. Expand the right boundary to include incoming status states, and contract the left boundary whenever invalid status constraints are violated. Keep track of the optimal window length across the traversal.

**Step-by-Step Reasoning:**
1. Initialize two pointers, left and right, at the start of the status array.
2. Iterate right pointer from index 0 to n - 1, incorporating each status into the current window state.
3. If the current window violates the valid status invariant (e.g., exceeds permitted fault threshold), increment left pointer until the invariant is restored.
4. Update the maximum length observed so far with (right - left + 1).
5. Return the maximum valid contiguous status length upon termination.

**Why It Works:**
Both pointers move monotonically from left to right across the sequence. Because each element enters the window once and leaves at most once, the window captures all maximal valid contiguous subsegments without redundant re-evaluation.

### Time Complexity

O(n)

### Space Complexity

O(1)

## 4. Java Solution

### Required Concepts

- BufferedReader
- Two Pointers
- Sliding Window
- Math.max

### AI-Generated Java Implementation

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.StringTokenizer;

public class Solution {
    public static int maxConsecutiveStatus(int[] statuses, int k) {
        int left = 0;
        int zeroCount = 0;
        int maxLength = 0;

        for (int right = 0; right < statuses.length; right++) {
            if (statuses[right] == 0) {
                zeroCount++;
            }
            while (zeroCount > k) {
                if (statuses[left] == 0) {
                    zeroCount--;
                }
                left++;
            }
            maxLength = Math.max(maxLength, right - left + 1);
        }

        return maxLength;
    }

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String line = br.readLine();
        if (line == null || line.trim().isEmpty()) {
            return;
        }
        StringTokenizer st = new StringTokenizer(line);
        int n = Integer.parseInt(st.nextToken());
        int k = Integer.parseInt(st.nextToken());

        int[] statuses = new int[n];
        st = new StringTokenizer(br.readLine());
        for (int i = 0; i < n; i++) {
            statuses[i] = Integer.parseInt(st.nextToken());
        }

        System.out.println(maxConsecutiveStatus(statuses, k));
    }
}
```

## 5. Python Solution

### Required Concepts

- sys.stdin
- Sliding Window
- Monotonic Pointers
- Greedy Maintenance

### AI-Generated Python Implementation

```python
import sys

def max_consecutive_status(statuses, k):
    left = 0
    zero_count = 0
    max_length = 0

    for right in range(len(statuses)):
        if statuses[right] == 0:
            zero_count += 1
        while zero_count > k:
            if statuses[left] == 0:
                zero_count -= 1
            left += 1
        max_length = max(max_length, right - left + 1)

    return max_length

def main():
    input_data = sys.stdin.read().split()
    if not input_data:
        return
    n = int(input_data[0])
    k = int(input_data[1])
    statuses = [int(x) for x in input_data[2:2 + n]]
    print(max_consecutive_status(statuses, k))

if __name__ == '__main__':
    main()
```

## 6. C++ Solution

### Required Concepts

- std::vector
- Two Pointers
- Fast I/O
- Sliding Window Invariant

### Original Accepted Submission

```cpp
// Original code preserved from Codeforces
```

### AI-Generated C++ Alternative

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

int maxConsecutiveStatus(const std::vector<int>& statuses, int k) {
    int left = 0;
    int zero_count = 0;
    int max_length = 0;

    for (int right = 0; right < static_cast<int>(statuses.size()); ++right) {
        if (statuses[right] == 0) {
            ++zero_count;
        }
        while (zero_count > k) {
            if (statuses[left] == 0) {
                --zero_count;
            }
            ++left;
        }
        max_length = std::max(max_length, right - left + 1);
    }

    return max_length;
}

int main() {
    std::ios_base::sync_with_stdio(false);
    std::cin.tie(nullptr);

    int n, k;
    if (std::cin >> n >> k) {
        std::vector<int> statuses(n);
        for (int i = 0; i < n; ++i) {
            std::cin >> statuses[i];
        }
        std::cout << maxConsecutiveStatus(statuses, k) << "\n";
    }
    return 0;
}
```

## 7. Rust Solution

### Required Concepts

- std::io
- Vec<i32>
- usize indexing
- std::cmp::max

### AI-Generated Rust Implementation

```rust
use std::io::{self, Read};
use std::cmp::max;

fn max_consecutive_status(statuses: &[i32], k: i32) -> usize {
    let mut left = 0;
    let mut zero_count = 0;
    let mut max_length = 0;

    for right in 0..statuses.len() {
        if statuses[right] == 0 {
            zero_count += 1;
        }
        while zero_count > k {
            if statuses[left] == 0 {
                zero_count -= 1;
            }
            left += 1;
        }
        max_length = max(max_length, right - left + 1);
    }

    max_length
}

fn main() {
    let mut input = String::new();
    if io::stdin().read_to_string(&mut input).is_ok() {
        let mut tokens = input.split_whitespace();
        if let (Some(n_str), Some(k_str)) = (tokens.next(), tokens.next()) {
            let n: usize = n_str.parse().unwrap_or(0);
            let k: i32 = k_str.parse().unwrap_or(0);
            let mut statuses = Vec::with_capacity(n);
            for _ in 0..n {
                if let Some(tok) = tokens.next() {
                    statuses.push(tok.parse::<i32>().unwrap_or(0));
                }
            }
            let ans = max_consecutive_status(&statuses, k);
            println!("{}", ans);
        }
    }
}
```

## Original C++ Accepted Submission

### Preserved User Submission

```c
// Original code preserved from Codeforces
```

## 8. Motivation

> "Mastery in algorithm design is achieved not by memorizing answers, but by recognizing invariants and moving boundaries with precision."

<div align="center">

## Thank You 🚀

</div>
