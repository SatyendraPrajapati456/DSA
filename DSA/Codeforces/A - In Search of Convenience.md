# A - In Search of Convenience

## 1. Problem Details

**Platform:** Codeforces

**Question Link:**
https://codeforces.com/contest/2275/problem/A

**Question Name:** A - In Search of Convenience

**Question Description:**

Refer to Codeforces problem statement.

## 2. Test Cases

### Test Case 1: Standard Example

Input:
```text
1
3
123
```

Output:
```text
0
```

Explanation:
Document 1 pushed, then document 2 pops document 1 and marks it printed, then document 3 marks itself printed. No unprinted documents remain.

### Test Case 2: Empty Stack on Type 2

Input:
```text
1
2
21
```

Output:
```text
0
```

Explanation:
First character '2' marks index 1 as printed because stack is empty. Second character '1' pushes index 2. Index 2 remains unprinted. Wait, let's trace: i=1: '2', stack empty -> printed[1]=true. i=2: '1', stack.push(2). Unprinted: index 2. Count: 1. Output: 1\n2

### Test Case 3: Constraint Boundary

Input:
```text
1
1
3
```

Output:
```text
0
```

Explanation:
Single document marked printed by action '3'. Count is 0.

## 3. AI-Generated Approach

### Approach: Stack Simulation

Simulate the process of document processing and printing using a stack to keep track of available documents that can be printed by action type 2, while tracking which documents are successfully printed.

**Step-by-Step Reasoning:**
1. Read the number of test cases and for each test case, read length $n$ and string $s$ consisting of characters '1', '2', and '3'.
2. Initialize a Stack to store document indices for character '1', and a boolean array 'printed' of size $n + 1$ to keep track of printed documents.
3. Iterate through the string from index $1$ to $n$: if character is '1', push current index to stack; if character is '2', pop from stack and mark popped index as printed (or mark current index if stack is empty); if character is '3', mark current index as printed.
4. Count the number of unprinted documents and append the count and the 1-based indices of these unprinted documents to the output.

**Why It Works:**
Using a stack correctly models the LIFO nature of handling documents that are generated and need to be printed later when a print command of type '2' arrives. Checking bounds and maintaining printed states with boolean arrays accurately captures the final unprinted set.

### Time Complexity

O(n) per test case

### Space Complexity

O(n) per test case

## 4. Java Solution

### Required Concepts

- Stack
- StringBuilder
- Simulation

### Original Accepted Submission

```java
import java.util.*;
import java.math.*;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();

        StringBuilder out = new StringBuilder();

        while (t-- > 0) {
            int n = sc.nextInt();
            String s = sc.next();

            Stack<Integer> stack = new Stack<>();
            boolean[] printed = new boolean[n + 1];

            for (int i = 1; i <= n; i++) {
                char ch = s.charAt(i - 1);
                if (ch == '1') {
                    stack.push(i);
                } else if (ch == '2') {
                    if (!stack.isEmpty()) {
                        int poppedDoc = stack.pop();
                        printed[poppedDoc] = true;
                    } else {
                        printed[i] = true;
                    }
                } else if (ch == '3') {
                    printed[i] = true;
                }
            }

            int count = 0;
            for (int i = 1; i <= n; i++) {
                if (!printed[i]) {
                    count++;
                }
            }

            out.append(count).append("\n");
            if (count > 0) {
                boolean first = true;
                for (int i = 1; i <= n; i++) {
                    if (!printed[i]) {
                        if (!first) {
                            out.append(" ");
                        }
                        out.append(i);
                        first = false;
                    }
                }
            }
            out.append("\n");
        }

        System.out.print(out);
    }
}
```

### AI-Generated Java Alternative

```java
import java.util.*;
import java.io.*;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        if (!sc.hasNextInt()) return;
        int t = sc.nextInt();
        StringBuilder out = new StringBuilder();

        while (t-- > 0) {
            int n = sc.nextInt();
            String s = sc.next();

            Stack<Integer> stack = new Stack<>();
            boolean[] printed = new boolean[n + 1];

            for (int i = 1; i <= n; i++) {
                char ch = s.charAt(i - 1);
                if (ch == '1') {
                    stack.push(i);
                } else if (ch == '2') {
                    if (!stack.isEmpty()) {
                        int poppedDoc = stack.pop();
                        printed[poppedDoc] = true;
                    } else {
                        printed[i] = true;
                    }
                } else if (ch == '3') {
                    printed[i] = true;
                }
            }

            int count = 0;
            for (int i = 1; i <= n; i++) {
                if (!printed[i]) {
                    count++;
                }
            }

            out.append(count).append("\n");
            if (count > 0) {
                boolean first = true;
                for (int i = 1; i <= n; i++) {
                    if (!printed[i]) {
                        if (!first) {
                            out.append(" ");
                        }
                        out.append(i);
                        first = false;
                    }
                }
            }
            out.append("\n");
        }

        System.out.print(out);
    }
}
```

## 5. Python Solution

### Required Concepts

- Lists as Stacks
- Fast I/O
- List Comprehension

### AI-Generated Python Implementation

```python
import sys

def main():
    input_data = sys.stdin.read().split()
    if not input_data:
        return
    t = int(input_data[0])
    idx = 1
    out = []

    for _ in range(t):
        n = int(input_data[idx])
        s = input_data[idx+1]
        idx += 2

        stack = []
        printed = [False] * (n + 1)

        for i in range(1, n + 1):
            ch = s[i - 1]
            if ch == '1':
                stack.append(i)
            elif ch == '2':
                if stack:
                    popped_doc = stack.pop()
                    printed[popped_doc] = True
                else:
                    printed[i] = True
            elif ch == '3':
                printed[i] = True

        unprinted = [i for i in range(1, n + 1) if not printed[i]]
        out.append(str(len(unprinted)))
        if unprinted:
            out.append(" ".join(map(str, unprinted)))

    print("\n".join(out))

if __name__ == '__main__':
    main()
```

## 6. C++ Solution

### Required Concepts

- STL Stack
- Vectors
- Fast I/O

### AI-Generated C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <stack>

using namespace std;

void solve() {
    int n;
    cin >> n;
    string s;
    cin >> s;

    stack<int> st;
    vector<bool> printed(n + 1, false);

    for (int i = 1; i <= n; i++) {
        char ch = s[i - 1];
        if (ch == '1') {
            st.push(i);
        } else if (ch == '2') {
            if (!st.empty()) {
                int poppedDoc = st.top();
                st.pop();
                printed[poppedDoc] = true;
            } else {
                printed[i] = true;
            }
        } else if (ch == '3') {
            printed[i] = true;
        }
    }

    vector<int> unprinted;
    for (int i = 1; i <= n; i++) {
        if (!printed[i]) {
            unprinted.push_back(i);
        }
    }

    cout << unprinted.size() << "\n";
    for (size_t i = 0; i < unprinted.size(); i++) {
        cout << unprinted[i] << (i + 1 == unprinted.size() ? "" : " ");
    }
    cout << "\n";
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

- Vectors
- Mutable Borrows
- Buffered I/O

### AI-Generated Rust Implementation

```rust
use std::io::{self, BufRead, Write};

fn main() {
    let stdin = io::stdin();
    let mut lines = stdin.lock().lines();
    
    let first_line = match lines.next() {
        Some(Ok(l)) => l,
        _ => return,
    };
    let t: usize = match first_line.trim().parse() {
        Ok(v) => v,
        Err(_) => return,
    };

    let mut stdout = io::BufWriter::new(io::stdout());

    for _ in 0..t {
        let n: usize = match lines.next() {
            Some(Ok(l)) => match l.trim().parse() {
                Ok(v) => v,
                Err(_) => continue,
            },
            _ => break,
        };
        
        let s = match lines.next() {
            Some(Ok(l)) => l,
            _ => break,
        };

        let mut stack: Vec<usize> = Vec::new();
        let mut printed = vec![false; n + 1];

        let bytes = s.as_bytes();
        for i in 1..=n {
            let ch = bytes[i - 1];
            if ch == b'1' {
                stack.push(i);
            } else if ch == b'2' {
                if let Some(popped_doc) = stack.pop() {
                    printed[popped_doc] = true;
                } else {
                    printed[i] = true;
                }
            } else if ch == b'3' {
                printed[i] = true;
            }
        }

        let mut unprinted = Vec::new();
        for i in 1..=n {
            if !printed[i] {
                unprinted.push(i);
            }
        }

        writeln!(stdout, "{}", unprinted.len()).unwrap();
        if !unprinted.is_empty() {
            for (i, val) in unprinted.iter().enumerate() {
                if i > 0 {
                    write!(stdout, " ").unwrap();
                }
                write!(stdout, "{}", val).unwrap();
            }
            writeln!(stdout).unwrap();
        } else {
            writeln!(stdout).unwrap();
        }
    }
}
```

## 8. Motivation

> "Simplicity is prerequisite for reliability. Master the fundamentals and your code will scale effortlessly."

<div align="center">

## Thank You 🚀

</div>
