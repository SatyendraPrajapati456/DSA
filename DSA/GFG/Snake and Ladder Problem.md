# Snake and Ladder Problem

## 1. Problem Details

**Platform:** GeeksforGeeks

**Question Link:**
https://www.geeksforgeeks.org/problems/snake-and-ladder-problem4816/1

**Question Name:** Snake and Ladder Problem

**Question Description:**

Refer to GeeksforGeeks problem statement.

## 2. Test Cases

### Test Case 1: Standard Example with Ladders and Snakes

Input:
```text
N = 8, arr = [3, 22, 5, 8, 11, 26, 20, 29, 17, 4, 19, 7, 27, 1, 21, 9]
```

Output:
```text
3
```

Explanation:
From 1, roll 2 to reach cell 3, which takes the ladder to 22. From 22, roll 5 to reach 27, which slides down to 1. Alternatively, from 22 roll 6 to reach 28, then roll 2 to reach 30, resulting in 3 moves.

### Test Case 2: Direct Ladder Path

Input:
```text
N = 1, arr = [2, 30]
```

Output:
```text
1
```

Explanation:
From cell 1, rolling a 1 moves to cell 2, which has a ladder directly to cell 30 in a single move.

### Test Case 3: No Ladders or Snakes

Input:
```text
N = 0, arr = []
```

Output:
```text
5
```

Explanation:
From cell 1, rolling 6 five times reaches 7, 13, 19, 25, and then rolling 5 reaches 30, taking a minimum of 5 moves (e.g., 1 -> 7 -> 13 -> 19 -> 25 -> 30, or using rolls that sum to 29).

## 3. AI-Generated Approach

### Approach: Breadth-First Search (BFS)

Model the board as an unweighted directed graph where each cell is a vertex and each valid roll of a 6-sided die corresponds to a directed edge of weight 1. Finding the minimum number of dice throws to reach the final cell (cell 30) from the starting cell (cell 1) is equivalent to finding the shortest path in an unweighted graph, which BFS solves optimally.

**Step-by-Step Reasoning:**
1. Initialize an array `jump` of size 31 with -1 to record ladder and snake destinations.
2. Populate `jump` using the input ladder and snake pairs such that `jump[u] = v`.
3. Use a queue for BFS and a boolean array `visited` of size 31 to avoid revisiting cells.
4. Enqueue starting cell 1, mark it as visited, and initialize `moves = 0`.
5. Process the queue level by level. For each node, if it equals cell 30, return `moves`.
6. For each dice outcome from 1 to 6, calculate `next = current + dice`. If `next > 30`, stop exploring further dice rolls.
7. If `jump[next] != -1`, update `next` to `jump[next]`. If `next` is not visited, mark it visited and enqueue it.
8. Increment `moves` after finishing each level. If the queue is exhausted without reaching cell 30, return -1.

**Why It Works:**
BFS explores vertices in increasing order of their distance from the source vertex. Since every die roll represents an edge with an identical weight of 1, the first time the destination cell is dequeued (or reached), it is guaranteed to be via the minimum number of moves.

### Time Complexity

O(V + E) where V = 30 is the number of cells and E <= 6 * V is the number of transitions, which simplifies to O(1) for a fixed 30-cell board.

### Space Complexity

O(V) where V = 30 for the BFS queue, visited array, and jump lookup table, simplifying to O(1) for a fixed 30-cell board.

## 4. Java Solution

### Required Concepts

- Queue / ArrayDeque
- Level-order BFS traversal
- Graph modeling

### Original Accepted Submission

```java
int size = queue.size();

             while (size-- > 0) {

                 int current = queue.poll();

                 // Reached destination
                 if (current == N) {
                     return moves;
                 }

                 // Dice: 1 to 6
                 for (int dice = 1; dice <= 6; dice++) {

                     int next = current + dice;

                     if (next > N)
                         break;

                     // Snake or ladder
                     if (jump[next] != -1) {
                         next = jump[next];
                     }

                     if (!visited[next]) {
                         visited[next] = true;
                         queue.offer(next);
                     }
                 }
             }

             moves++;
         }

         return -1;
     }
 }
```

### AI-Generated Java Alternative

```java
import java.util.*;

class Solution {
    static int minThrow(int N, int arr[]) {
        int target = 30;
        int[] jump = new int[target + 1];
        Arrays.fill(jump, -1);
        
        for (int i = 0; i < 2 * N; i += 2) {
            jump[arr[i]] = arr[i + 1];
        }
        
        boolean[] visited = new boolean[target + 1];
        Queue<Integer> queue = new ArrayDeque<>();
        
        queue.offer(1);
        visited[1] = true;
        int moves = 0;
        
        while (!queue.isEmpty()) {
            int size = queue.size();
            
            while (size-- > 0) {
                int current = queue.poll();
                
                if (current == target) {
                    return moves;
                }
                
                for (int dice = 1; dice <= 6; dice++) {
                    int next = current + dice;
                    if (next > target) {
                        break;
                    }
                    
                    if (jump[next] != -1) {
                        next = jump[next];
                    }
                    
                    if (!visited[next]) {
                        visited[next] = true;
                        queue.offer(next);
                    }
                }
            }
            moves++;
        }
        
        return -1;
    }
}
```

## 5. Python Solution

### Required Concepts

- collections.deque
- BFS shortest path
- Level-by-level queue processing

### AI-Generated Python Implementation

```python
from collections import deque

class Solution:
    def minThrow(self, N, arr):
        target = 30
        jump = [-1] * (target + 1)
        
        for i in range(0, 2 * N, 2):
            jump[arr[i]] = arr[i + 1]
            
        visited = [False] * (target + 1)
        queue = deque([1])
        visited[1] = True
        moves = 0
        
        while queue:
            size = len(queue)
            for _ in range(size):
                current = queue.popleft()
                
                if current == target:
                    return moves
                
                for dice in range(1, 7):
                    nxt = current + dice
                    if nxt > target:
                        break
                    
                    if jump[nxt] != -1:
                        nxt = jump[nxt]
                    
                    if not visited[nxt]:
                        visited[nxt] = True
                        queue.append(nxt)
            moves += 1
            
        return -1
```

## 6. C++ Solution

### Required Concepts

- std::queue
- std::vector
- Breadth-First Search

### AI-Generated C++ Implementation

```cpp
#include <vector>
#include <queue>

class Solution {
public:
    int minThrow(int N, int arr[]) {
        int target = 30;
        std::vector<int> jump(target + 1, -1);
        
        for (int i = 0; i < 2 * N; i += 2) {
            jump[arr[i]] = arr[i + 1];
        }
        
        std::vector<bool> visited(target + 1, false);
        std::queue<int> q;
        
        q.push(1);
        visited[1] = true;
        int moves = 0;
        
        while (!q.empty()) {
            int size = q.size();
            
            while (size-- > 0) {
                int current = q.front();
                q.pop();
                
                if (current == target) {
                    return moves;
                }
                
                for (int dice = 1; dice <= 6; ++dice) {
                    int next = current + dice;
                    if (next > target) {
                        break;
                    }
                    
                    if (jump[next] != -1) {
                        next = jump[next];
                    }
                    
                    if (!visited[next]) {
                        visited[next] = true;
                        q.push(next);
                    }
                }
            }
            moves++;
        }
        
        return -1;
    }
};
```

## 7. Rust Solution

### Required Concepts

- VecDeque
- usize indexing
- Shortest path on unweighted graphs

### AI-Generated Rust Implementation

```rust
use std::collections::VecDeque;

pub struct Solution;

impl Solution {
    pub fn min_throw(n: i32, arr: &[i32]) -> i32 {
        let target: usize = 30;
        let mut jump = vec![-1i32; target + 1];
        
        let total_pairs = (n as usize) * 2;
        for i in (0..total_pairs).step_by(2) {
            let from = arr[i] as usize;
            let to = arr[i + 1];
            jump[from] = to;
        }
        
        let mut visited = vec![false; target + 1];
        let mut queue = VecDeque::new();
        
        queue.push_back(1usize);
        visited[1] = true;
        let mut moves = 0;
        
        while !queue.is_empty() {
            let size = queue.len();
            
            for _ in 0..size {
                let current = queue.pop_front().unwrap();
                
                if current == target {
                    return moves;
                }
                
                for dice in 1..=6 {
                    let mut next = current + dice;
                    if next > target {
                        break;
                    }
                    
                    if jump[next] != -1 {
                        next = jump[next] as usize;
                    }
                    
                    if !visited[next] {
                        visited[next] = true;
                        queue.push_back(next);
                    }
                }
            }
            moves += 1;
        }
        
        -1
    }
}
```

## 8. Motivation

> "In the game of algorithms, as in Snake and Ladder, setbacks are just transitions. Stay on the BFS path: explore methodically, never skip a step, and every obstacle will eventually yield to the shortest path forward."

<div align="center">

## Thank You 🚀

</div>
