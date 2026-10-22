# LARGESECOND

## 1. Problem Details

**Platform:** CodeChef

**Question Link:**
https://www.codechef.com/practice/course/arrays-new/ARRAYSP01/problems/LARGESECOND

**Question Name:** LARGESECOND

**Question Description:**

Switch to AI Tutor Mode

New

Largest and Second Largest

You are given an array AAA of NNN integers.

Find the maximum sum of two distinct integers in the array.

Note: It is guaranteed that there exist at least two distinct integers in the array.

Input Format

• The first line of input will contain a single integer TTT, denoting the number of test cases.

• Each test case consists of multiple lines of input.

• The first line of each test case contains single integer NNN — the size of the array.

• The next line contains NNN space-separated integers, denoting the array AAA.

Output Format

For each test case, output on a new line, the maximum sum of two distinct integers in the array.

Constraints

• 1≤T≤10001 \leq T \leq 10001≤T≤1000

• 2≤N≤1052 \leq N \leq 10^52≤N≤105

• 1≤Ai≤10001 \leq A_i \leq 10001≤Ai​≤1000

• The sum of NNN over all test cases does not exceed 2⋅1052\cdot 10^52⋅105.

Sample 1:

Input

Output

4
3
4 1 6
7
3 7 2 1 1 5 3
5
8 2 9 4 9
2
1 2

10
12
17
3

Explanation:

Test case 111: The maximum sum of two distinct elements is 4+6=104 + 6 = 104+6=10 .

Test case 222: The maximum sum of two distinct elements is 7+5=127 + 5 = 127+5=12.

Test case 333: The maximum sum of two distinct elements is 8+9=178 + 9 = 178+9=17.

Test case 444: The maximum sum of two distinct elements is 1+2=31 + 2 = 31+2=3.

Did you like the problem?

310 users found this helpful

AI Tutor

English

Introducing multiple AI Chat Languages✨

Now Chat in your language! Select from the dropdown

Welcome to the CodeChef AI Tutor

I am your problem-solving companion.

We will begin by understanding the problem together, then explore different ways to solve it.
Share any ideas you have — and I will help you refine and build on them.

Ready to get started?

Add my Code

## 2. Test Cases

### Test Case 1: Standard Example 1

Input:
```text
1
3
4 1 6
```

Output:
```text
10
```

Explanation:
Max is 6 and second distinct largest is 4. Sum = 4 + 6 = 10.

### Test Case 2: Duplicates Present

Input:
```text
1
5
8 2 9 4 9
```

Output:
```text
17
```

Explanation:
Max is 9, second largest distinct is 8 (ignoring duplicate 9). Sum = 8 + 9 = 17.

### Test Case 3: Minimum Size

Input:
```text
1
2
1 2
```

Output:
```text
3
```

Explanation:
Max is 2, second is 1. Sum = 1 + 2 = 3.

## 3. AI-Generated Approach

### Approach: Single Pass Track Maximums

Find the largest and second largest distinct integers in a single pass through the array by maintaining two variables for the top two unique maximum values.

**Step-by-Step Reasoning:**
1. Initialize 'max' and 'second' to minimum possible integer values.
2. Iterate through each element 'x' in the array.
3. If 'x' is strictly greater than 'max', update 'second' to 'max' and 'max' to 'x'.
4. Else if 'x' is less than 'max' and strictly greater than 'second', update 'second' to 'x'.
5. After checking all elements, output the sum of 'max' and 'second'.

**Why It Works:**
By maintaining the two highest distinct values seen so far, we guarantee that 'max' holds the absolute maximum element and 'second' holds the highest element strictly smaller than 'max'. Since the problem guarantees the existence of at least two distinct integers, 'second' will always be properly populated.

### Time Complexity

O(N)

### Space Complexity

O(1)

## 4. Java Solution

### Required Concepts

- Primitive types
- Conditional branching
- Single-pass optimization

### Original Accepted Submission

```java
while (t-- > 0) {
            int n = scanner.nextInt();

            int max = Integer.MIN_VALUE;
            int second = Integer.MIN_VALUE;

            for (int i = 0; i < n; i++) {
                int x = scanner.nextInt();

                if (x > max) {
                    second = max;
                    max = x;
                } else if (x < max && x > second) {
                    second = x;
                }
            }

            System.out.println(max + second);
        }

        scanner.close();
    }
}
```

### AI-Generated Java Alternative

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        if (!scanner.hasNextInt()) return;
        int t = scanner.nextInt();
        while (t-- > 0) {
            int n = scanner.nextInt();
            int max = Integer.MIN_VALUE;
            int second = Integer.MIN_VALUE;

            for (int i = 0; i < n; i++) {
                int x = scanner.nextInt();
                if (x > max) {
                    second = max;
                    max = x;
                } else if (x < max && x > second) {
                    second = x;
                }
            }
            System.out.println(max + second);
        }
        scanner.close();
    }
}
```

## 5. Python Solution

### Required Concepts

- Generators
- Standard input parsing
- Greedy selection

### AI-Generated Python Implementation

```python
import sys

def solve():
    input_data = sys.stdin.read().split()
    if not input_data:
        return
    t = int(input_data[0])
    idx = 1
    for _ in range(t):
        n = int(input_data[idx])
        idx += 1
        max_val = -1
        second_val = -1
        for _ in range(n):
            x = int(input_data[idx])
            idx += 1
            if x > max_val:
                second_val = max_val
                max_val = x
            elif x < max_val and x > second_val:
                second_val = x
        print(max_val + second_val)

if __name__ == '__main__':
    solve()
```

## 6. C++ Solution

### Required Concepts

- I/O optimization
- Variable shadowing avoidance
- Greedy approach

### AI-Generated C++ Implementation

```cpp
#include <iostream>
#include <climits>

using namespace std;

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    
    int t;
    if (!(cin >> t)) return 0;
    
    while (t--) {
        int n;
        cin >> n;
        int max_val = INT_MIN;
        int second_val = INT_MIN;
        
        for (int i = 0; i < n; i++) {
            int x;
            cin >> x;
            if (x > max_val) {
                second_val = max_val;
                max_val = x;
            } else if (x < max_val && x > second_val) {
                second_val = x;
            }
        }
        cout << (max_val + second_val) << "\n";
    }
    return 0;
}
```

## 7. Rust Solution

### Required Concepts

- Iterator methods
- Buffered reading
- Error handling on parse

### AI-Generated Rust Implementation

```rust
use std::io::{self, BufRead};

fn main() {
    let stdin = io::stdin();
    let mut lines = stdin.lock().lines();
    
    let first_line = match lines.next() {
        Some(Ok(l)) => l,
        _ => return,
    };
    
    let mut tokens = first_line.split_whitespace();
    let t: usize = match tokens.next() {
        Some(v) => v.parse().unwrap(),
        None => return,
    };
    
    let mut all_tokens = Vec::new();
    for line in lines {
        if let Ok(l) = line {
            for s in l.split_whitespace() {
                all_tokens.push(s.to_string());
            }
        }
    }
    
    let mut idx = 0;
    for _ in 0..t {
        if idx >= all_tokens.len() { break; }
        let n: usize = all_tokens[idx].parse().unwrap();
        idx += 1;
        
        let mut max_val = i32::MIN;
        let mut second_val = i32::MIN;
        
        for _ in 0..n {
            let x: i32 = all_tokens[idx].parse().unwrap();
            idx += 1;
            
            if x > max_val {
                second_val = max_val;
                max_val = x;
            } else if x < max_val && x > second_val {
                second_val = x;
            }
        }
        println!("{}", max_val + second_val);
    }
}
```

## 8. Motivation

> "Excellence is not an act, but a habit. Keep coding, keep optimizing, and mastery will follow."

<div align="center">

## Thank You 🚀

</div>
