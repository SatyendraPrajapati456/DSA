# Status

## 1. Problem Details

**Platform:** Codeforces

**Question Link:**
https://codeforces.com/problemset/status

**Question Name:** Status

**Question Description:**

Refer to Codeforces problem statement.

## 2. Test Cases

### Test Case 1: Standard Example with Moderate Budget

Input:
```text
5 1
1 0 1 1 0
```

Output:
```text
4
```

Explanation:
Replacing or tolerating the zero at index 1 allows the window [0..3] to span length 4.

### Test Case 2: Edge Case - All Faulty States

Input:
```text
4 2
0 0 0 0
```

Output:
```text
2
```

Explanation:
With at most 2 replacements permitted, the maximum valid contiguous segment has length 2.

### Test Case 3: Constraint Boundary - Zero Budget with All Operational

Input:
```text
5 0
1 1 1 1 1
```

Output:
```text
5
```

Explanation:
No faults exist and budget is 0, so the entire array of length 5 is valid.

## 3. AI-Generated Approach

### Approach: Sliding Window / Two Pointers

Track the frequency of invalid status indicators within an expanding contiguous window. Whenever the count of faulty states exceeds the allowed threshold k, shrink the window from the left until the invariant is restored.

**Step-by-Step Reasoning:**
1. Initialize left pointer to 0, zeroCount to 0, and maxLen to 0.
2. Iterate through the array with right pointer from 0 to n - 1.
3. If the element at right indicates a faulty status (0), increment zeroCount.
4. While zeroCount exceeds the permitted budget k, check if the element at left is 0 and decrement zeroCount accordingly, then advance left.
5. Update maxLen with the current valid window length (right - left + 1).
6. Return or print maxLen after processing all elements.

**Why It Works:**
Because all elements in the window are contiguous and the window monotonically expands and contracts, every valid maximal subarray ending at each index is considered. Since both left and right pointers advance at most n times, correctness is maintained in linear time.

### Time Complexity

O(n)

### Space Complexity

O(1)

## 4. Java Solution

### Required Concepts

- BufferedReader
- Two Pointers
- Math.max

### AI-Generated Java Implementation

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String line = br.readLine();
        if (line == null || line.trim().isEmpty()) return;

        StringTokenizer st = new StringTokenizer(line);
        int n = Integer.parseInt(st.nextToken());
        int k = Integer.parseInt(st.nextToken());

        int[] a = new int[n];
        st = new StringTokenizer(br.readLine());
        for (int i = 0; i < n; i++) {
            a[i] = Integer.parseInt(st.nextToken());
        }

        int left = 0;
        int zeroCount = 0;
        int maxLen = 0;

        for (int right = 0; right < n; right++) {
            if (a[right] == 0) {
                zeroCount++;
            }
            while (zeroCount > k) {
                if (a[left] == 0) {
                    zeroCount--;
                }
                left++;
            }
            maxLen = Math.max(maxLen, right - left + 1);
        }

        System.out.println(maxLen);
    }
}
```

## 5. Python Solution

### Required Concepts

- sys.stdin.read
- Sliding Window
- In-place Pointers

### AI-Generated Python Implementation

```python
import sys

def main():
    input_data = sys.stdin.read().split()
    if not input_data:
        return

    n = int(input_data[0])
    k = int(input_data[1])
    a = [int(x) for x in input_data[2:2 + n]]

    left = 0
    zero_count = 0
    max_len = 0

    for right in range(n):
        if a[right] == 0:
            zero_count += 1
        while zero_count > k:
            if a[left] == 0:
                zero_count -= 1
            left += 1
        max_len = max(max_len, right - left + 1)

    print(max_len)

if __name__ == '__main__':
    main()
```

## 6. C++ Solution

### Required Concepts

- std::vector
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

using namespace std;

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    int n, k;
    if (!(cin >> n >> k)) return 0;

    vector<int> a(n);
    for (int i = 0; i < n; ++i) {
        cin >> a[i];
    }

    int left = 0;
    int zero_count = 0;
    int max_len = 0;

    for (int right = 0; right < n; ++right) {
        if (a[right] == 0) {
            zero_count++;
        }
        while (zero_count > k) {
            if (a[left] == 0) {
                zero_count--;
            }
            left++;
        }
        max_len = max(max_len, right - left + 1);
    }

    cout << max_len << "\n";
    return 0;
}
```

## 7. Rust Solution

### Required Concepts

- Iterator chaining
- Option handling
- usize indexing

### AI-Generated Rust Implementation

```rust
use std::io::{self, Read};

fn main() {
    let mut input = String::new();
    if io::stdin().read_to_string(&mut input).is_err() {
        return;
    }
    let mut iter = input.split_whitespace();
    let n: usize = match iter.next() {
        Some(val) => val.parse().unwrap(),
        None => return,
    };
    let k: usize = iter.next().unwrap().parse().unwrap();
    let a: Vec<i32> = iter.take(n).map(|x| x.parse().unwrap()).collect();

    let mut left = 0;
    let mut zero_count = 0;
    let mut max_len = 0;

    for right in 0..n {
        if a[right] == 0 {
            zero_count += 1;
        }
        while zero_count > k {
            if a[left] == 0 {
                zero_count -= 1;
            }
            left += 1;
        }
        max_len = max_len.max(right - left + 1);
    }

    println!("{}", max_len);
}
```

## Original C++ Accepted Submission

### Preserved User Submission

```c
// Original code preserved from Codeforces
```

## 8. Motivation

> "Mastery in competitive programming is not about avoiding errors, but about shrinking the window between encountering a failure and engineering its optimal resolution."

<div align="center">

## Thank You 🚀

</div>
