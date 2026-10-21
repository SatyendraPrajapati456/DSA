# Shortest Safe Route in Grid

## 1. Problem Details

**Question Link:** https://www.geeksforgeeks.org/problems/find-shortest-safe-route-in-a-matrix/1

**Question Name:** Shortest Safe Route in Grid

**Platform:** GeeksforGeeks  
**Problem ID:** find-shortest-safe-route-in-a-matrix  
**Accepted Submission:** Java (21)  
**Documented:** 2026-10-21 15:07 UTC

**Question Description:**

```text
Given a 2D matrix mat[][], where each cell is either 0 (landmine) or 1 (safe), find the minimum number of steps required to travel from any cell in the leftmost column to any cell in the rightmost column.

- You can move only in four directions: up, down, left, and right.
- A cell is unsafe if it contains a landmine or is directly adjacent (up, down, left, or right) to a landmine, and such cells must be avoided.
- Return -1 if no safe path exists.

Examples:

Input: mat[][] = [[1, 0, 1, 1, 1], [1, 1, 1, 1, 1], [1, 1, 1, 1, 1], [1, 1, 1, 0, 1], [1, 1, 1, 1, 0]]
[image]
Output: 6
Explanation: We can see that length of shortest safe route is 6.
[image]

Input: mat[][] = [[1, 1, 1, 1, 1], [1, 1, 0, 1, 1], [1, 1, 1, 1, 1]]
[image]
Output: -1
Explanation: There is no possible path from first column to last column.
```

*Problem text as provided by GeeksforGeeks, converted to plain text.*

## 2. Test Cases

Not generated. No AI provider is configured, so only your accepted solution is included. Add one in Settings and choose "Generate AI docs" to enrich this file.

## 3. Approach

Not generated. No AI provider is configured, so only your accepted solution is included. Add one in Settings and choose "Generate AI docs" to enrich this file.

## 4. Java Solution

### Original Accepted Submission

> Your code as submitted and accepted on GeeksforGeeks.

```java

class Solution {
    int shortestPath(int[][] mat) {
        int row = mat.length;
        int col = mat[0].length;

        boolean[][] unsafe = new boolean[row][col];

        // Mark landmines and cells adjacent to landmines
        for (int i = 0; i < row; i++) {
            for (int j = 0; j < col; j++) {
                if (mat[i][j] == 0) {

                    unsafe[i][j] = true;

                    if (isSafe(mat, i + 1, j)) {
                        unsafe[i + 1][j] = true;
                    }

                    if (isSafe(mat, i - 1, j)) {
                        unsafe[i - 1][j] = true;
                    }

                    if (isSafe(mat, i, j + 1)) {
                        unsafe[i][j + 1] = true;
                    }

                    if (isSafe(mat, i, j - 1)) {
                        unsafe[i][j - 1] = true;
                    }
                }
            }
        }

        Queue<int[]> q = new LinkedList<>();
        boolean[][] visited = new boolean[row][col];

        // Start from every safe cell in first column
        for (int i = 0; i < row; i++) {
            if (!unsafe[i][0]) {
                q.offer(new int[]{i, 0, 1});
                visited[i][0] = true;
            }
        }

        int[] dr = {-1, 1, 0, 0};
        int[] dc = {0, 0, -1, 1};

        while (!q.isEmpty()) {
            int[] curr = q.poll();

            int r = curr[0];
            int c = curr[1];
            int dist = curr[2];

            if (c == col - 1) {
                return dist;
            }

            for (int k = 0; k < 4; k++) {
                int nr = r + dr[k];
                int nc = c + dc[k];

                if (isSafe(mat, nr, nc) &&
                    !unsafe[nr][nc] &&
                    !visited[nr][nc]) {

                    visited[nr][nc] = true;
                    q.offer(new int[]{nr, nc, dist + 1});
                }
            }
        }

        return -1;
    }

    boolean isSafe(int[][] mat, int i, int j) {
        int row = mat.length;
        int col = mat[0].length;

        return i >= 0 && i < row && j >= 0 && j < col;
    }
}
```

## 5. Motivation

*Every problem you solve strengthens the way you think.*

<div align="center">

## Thank You 🚀

</div>
