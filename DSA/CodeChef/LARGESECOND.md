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

### Test Case 1: Standard Example with Duplicates

Input:
```text
N = 5
A = [8, 2, 9, 4, 9]
```

Output:
```text
17
```

Explanation:
The distinct elements are 8, 2, 9, 4. The largest is 9 and the second largest distinct element is 8. Their sum is 9 + 8 = 17.

### Test Case 2: Minimum Length Array

Input:
```text
N = 2
A = [1, 2]
```

Output:
```text
3
```

Explanation:
The only two distinct elements are 1 and 2. Their sum is 1 + 2 = 3.

### Test Case 3: Unsorted Array with Multiple Duplicates

Input:
```text
N = 7
A = [3, 7, 2, 1, 1, 5, 3]
```

Output:
```text
12
```

Explanation:
The distinct values are 1, 2, 3, 5, 7. The two largest distinct values are 7 and 5, producing a sum of 12.

## 3. AI-Generated Approach

### Approach: Set-Based Unique Element Extraction / Two Maximum Tracking

The user's code eliminates duplicates by inserting elements into a `HashSet`, converts the set into an `ArrayList`, and accesses the elements to compute the sum. More robustly and idiomatically, the problem seeks the two largest distinct numbers in the array. This can be solved either by sorting unique elements or by tracking the largest (`first`) and second largest (`second`) distinct values in a single pass.

**Step-by-Step Reasoning:**
1. Read the number of elements N for each test case.
2. Initialize two variables, `first` and `second`, to track the largest and second largest distinct integers encountered so far (initialized to negative infinity or -1 since elements are positive).
3. Iterate through each element in the array: if the current element is strictly greater than `first`, set `second = first` and update `first` to the current element.
4. Else if the current element is strictly less than `first` but strictly greater than `second`, update `second` to the current element.
5. Sum `first` and `second` and output the result.

**Why It Works:**
Since all elements are positive integers and we require the maximum sum of two distinct elements, the optimal pair is composed of the absolute maximum distinct value and the strictly smaller second largest distinct value. By maintaining the two largest distinct values encountered, we guarantee finding the optimal pair in a single pass without relying on hash set ordering or index assumptions.

### Time Complexity

O(N)

### Space Complexity

O(1)

## 4. Java Solution

### Required Concepts

- Single-pass traversal
- Duplicate filtering
- Fast I/O

### Original Accepted Submission

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();

        while (t-- > 0) {
            int n = scanner.nextInt();
            Set<Integer> s1=new HashSet<>();
            int max=0;

            for (int i = 0; i < n; i++) {
                s1.add(scanner.nextInt());
            }
            
            ArrayList<Integer> a1=new ArrayList<>(s1);
            System.out.println(a1.get(n-1)+a1.get(n-2));
           
        }
    }
}
```

### AI-Generated Java Alternative

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String line = br.readLine();
        if (line == null) return;
        int t = Integer.parseInt(line.trim());
        StringBuilder sb = new StringBuilder();

        while (t-- > 0) {
            int n = Integer.parseInt(br.readLine().trim());
            StringTokenizer st = new StringTokenizer(br.readLine());
            int first = -1;
            int second = -1;

            for (int i = 0; i < n; i++) {
                int val = Integer.parseInt(st.nextToken());
                if (val > first) {
                    second = first;
                    first = val;
                } else if (val > second && val != first) {
                    second = val;
                }
            }
            sb.append(first + second).append("\n");
        }
        System.out.print(sb);
    }
}
```

## 5. Python Solution

### Required Concepts

- Streaming tokenization
- Greedy two-max tracking
- sys.stdin.read

### AI-Generated Python Implementation

```python
import sys

def main():
    input_data = sys.stdin.read().split()
    if not input_data:
        return
    
    t = int(input_data[0])
    idx = 1
    results = []
    
    for _ in range(t):
        n = int(input_data[idx])
        idx += 1
        first = -1
        second = -1
        
        for _ in range(n):
            val = int(input_data[idx])
            idx += 1
            if val > first:
                second = first
                first = val
            elif val > second and val != first:
                second = val
                
        results.append(str(first + second))
        
    print("\n".join(results))

if __name__ == '__main__':
    main()
```

## 6. C++ Solution

### Required Concepts

- Competitive programming I/O
- Constant space optimization
- Conditional branching

### AI-Generated C++ Implementation

```cpp
#include <iostream>

using namespace std;

void solve() {
    int n;
    cin >> n;
    int first = -1, second = -1;
    for (int i = 0; i < n; ++i) {
        int val;
        cin >> val;
        if (val > first) {
            second = first;
            first = val;
        } else if (val > second && val != first) {
            second = val;
        }
    }
    cout << (first + second) << "\n";
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    int t;
    if (cin >> t) {
        while (t--) {
            solve();
        }
    }
    return 0;
}
```

## 7. Rust Solution

### Required Concepts

- BufRead
- Pattern matching
- Iterator traversal
- Type conversion

### AI-Generated Rust Implementation

```rust
use std::io::{self, BufRead};

fn main() {
    let stdin = io::stdin();
    let mut lines = stdin.lock().lines();

    if let Some(Ok(first_line)) = lines.next() {
        let t: usize = match first_line.trim().parse() {
            Ok(val) => val,
            Err(_) => return,
        };

        for _ in 0..t {
            let _n: usize = lines.next().unwrap().unwrap().trim().parse().unwrap();
            let arr_line = lines.next().unwrap().unwrap();
            let mut first: i32 = -1;
            let mut second: i32 = -1;

            for token in arr_line.split_whitespace() {
                let val: i32 = token.parse().unwrap();
                if val > first {
                    second = first;
                    first = val;
                } else if val > second && val != first {
                    second = val;
                }
            }

            println!("{}", first + second);
        }
    }
}
```

## 8. Motivation

> "Simplicity is the ultimate sophistication. Often the most robust algorithmic solution bypasses complex data structures in favor of a clean, linear observation."

<div align="center">

## Thank You 🚀

</div>
