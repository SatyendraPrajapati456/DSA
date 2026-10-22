# 2266C - AND, OR, Sort!

## 1. Problem Details

**Platform:** Codeforces

**Question Link:**
https://codeforces.com/problemset/problem/2266/C

**Question Name:** 2266C - AND, OR, Sort!

**Question Description:**

Refer to Codeforces problem statement.

## 2. Test Cases

### Test Case 1: Already Sorted

Input:
```text
1
3
001
```

Output:
```text
0
```

Explanation:
The string is already in non-decreasing order.

### Test Case 2: All Ones

Input:
```text
1
3
100
```

Output:
```text
2
```

Explanation:
Since s[0] is '1', all characters must be converted to '1' to maintain sorted order.

### Test Case 3: Mixed

Input:
```text
1
4
1010
```

Output:
```text
2
```

Explanation:
Optimal transformation results in 0011 or 0000 or 1111 depending on costs.

## 3. AI-Generated Approach

### Approach: Dynamic Programming

Maintain the minimum cost to transform the prefix of the string into a sorted state ending in either '0' or '1'.

**Step-by-Step Reasoning:**
1. Initialize dp0 (cost to end in '0') to 0 and dp1 (cost to end in '1') to infinity.
2. Iterate through the string, calculating the cost to flip the current character to '0' or '1'.
3. Update dp0 by adding the cost to make the current character '0'.
4. Update dp1 by taking the minimum of previous dp0 and dp1, then adding the cost to make the current character '1', provided a '1' is reachable.
5. The final answer is the minimum of the two DP states.

**Why It Works:**
Since the string must be sorted (all 0s followed by all 1s), the state at any index i only depends on whether the previous state ended in 0 or 1, allowing for a linear DP transition.

### Time Complexity

O(n)

### Space Complexity

O(1)

## 4. Java Solution

### Required Concepts

- Dynamic Programming
- Linear Scan
- Fast I/O

### Original Accepted Submission

```java
import java.util.Scanner;

public class Main {
    static final int INF = 1_000_000_000;

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        if (!sc.hasNextInt()) return;
        int t = sc.nextInt();

        StringBuilder sb = new StringBuilder();

        while (t-- > 0) {
            int n = sc.nextInt();
            String s = sc.next();

            // 1. Check if already sorted
            boolean sorted = true;
            for (int i = 0; i + 1 < n; ++i) {
                if (s.charAt(i) > s.charAt(i + 1)) {
                    sorted = false;
                    break;
                }
            }
            if (sorted) {
                sb.append(0).append("\n");
                continue;
            }

            // 2. Case s[0] == '1':
            // Since s[0] can never be changed to '0', the entire string must become '1's.
            if (s.charAt(0) == '1') {
                int zeros = 0;
                for (int i = 0; i < n; ++i) {
                    if (s.charAt(i) == '0') {
                        zeros++;
                    }
                }
                sb.append(zeros).append("\n");
                continue;
            }

            // 3. Case s[0] == '0': Dynamic Programming
            // dp0 = min ops to make s[0..i] sorted ending with '0'
            // dp1 = min ops to make s[0..i] sorted ending with '1'
            int dp0 = 0;
            int dp1 = INF; // Cannot place '1' until the first '1' is encountered in s

            for (int i = 0; i < n; i++) {
                char c = s.charAt(i);

                int costTo0 = (c == '1') ? 1 : 0;
                int costTo1 = (c == '0') ? 1 : 0;

                int nextDp0 = dp0 + costTo0;
                int nextDp1 = INF;

                // A '1' can be placed if:
                // - A '1' was already activated earlier (dp1 != INF), OR
                // - The current character is '1' (which makes it available)
                if (dp1 != INF || c == '1') {
                    int prevMin = Math.min(dp0, dp1);
                    if (prevMin != INF) {
                        nextDp1 = prevMin + costTo1;
                    }
                }

                dp0 = nextDp0;
                dp1 = nextDp1;
            }

            sb.append(Math.min(dp0, dp1)).append("\n");
        }

        // Print all outputs at once to keep I/O fast
        System.out.print(sb);
        sc.close();
    }
}
```

### AI-Generated Java Alternative

```java
import java.util.Scanner; public class Main { public static void main(String[] args) { Scanner sc = new Scanner(System.in); if (!sc.hasNextInt()) return; int t = sc.nextInt(); while (t-- > 0) { int n = sc.nextInt(); String s = sc.next(); int dp0 = 0, dp1 = 1000000000; for (char c : s.toCharArray()) { int costTo0 = (c == '1' ? 1 : 0); int costTo1 = (c == '0' ? 1 : 0); int nextDp0 = dp0 + costTo0; int nextDp1 = (dp1 == 1000000000 && c == '0') ? 1000000000 : Math.min(dp0, dp1) + costTo1; dp0 = nextDp0; dp1 = nextDp1; } System.out.println(Math.min(dp0, dp1)); } } }
```

## 5. Python Solution

### Required Concepts

- DP state management
- String iteration

### AI-Generated Python Implementation

```python
import sys
def solve():
    input = sys.stdin.read().split()
    idx = 1
    t = int(input[0])
    for _ in range(t):
        n = int(input[idx])
        s = input[idx+1]
        idx += 2
        dp0, dp1 = 0, float('inf')
        for c in s:
            cost0, cost1 = (1 if c == '1' else 0), (1 if c == '0' else 0)
            dp0, dp1 = dp0 + cost0, min(dp0, dp1) + cost1 if (dp1 != float('inf') or c == '1') else float('inf')
        print(min(dp0, dp1))
solve()
```

## 6. C++ Solution

### Required Concepts

- std::min
- std::string
- Complexity

### AI-Generated C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;
int main() {
    int t; cin >> t;
    while(t--) {
        int n; cin >> n;
        string s; cin >> s;
        int dp0 = 0, dp1 = 1e9;
        for(char c : s) {
            int cost0 = (c == '1'), cost1 = (c == '0');
            int next0 = dp0 + cost0;
            int next1 = (dp1 == 1e9 && c == '0') ? 1e9 : min(dp0, dp1) + cost1;
            dp0 = next0; dp1 = next1;
        }
        cout << min(dp0, dp1) << endl;
    }
    return 0;
}
```

## 7. Rust Solution

### Required Concepts

- Ownership
- Iterators
- Result handling

### AI-Generated Rust Implementation

```rust
use std::io::{self, BufRead};
fn main() {
    let stdin = io::stdin();
    let mut lines = stdin.lock().lines();
    let t: usize = lines.next().unwrap().unwrap().trim().parse().unwrap();
    for _ in 0..t {
        let _n: usize = lines.next().unwrap().unwrap().trim().parse().unwrap();
        let s = lines.next().unwrap().unwrap();
        let (mut dp0, mut dp1) = (0, 1_000_000_000);
        for c in s.chars() {
            let cost0 = if c == '1' { 1 } else { 0 };
            let cost1 = if c == '0' { 1 } else { 0 };
            let next0 = dp0 + cost0;
            let next1 = if dp1 == 1_000_000_000 && c == '0' { 1_000_000_000 } else { dp0.min(dp1) + cost1 };
            dp0 = next0; dp1 = next1;
        }
        println!("{}", dp0.min(dp1));
    }
}
```

## 8. Motivation

> "The expert in anything was once a beginner."

<div align="center">

## Thank You 🚀

</div>
