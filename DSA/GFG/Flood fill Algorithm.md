# Flood fill Algorithm

## 1. Problem Details

**Platform:** GeeksforGeeks

**Question Link:**
https://www.geeksforgeeks.org/problems/flood-fill-algorithm1856/1

**Question Name:** Flood fill Algorithm

**Question Description:**

Refer to GeeksforGeeks problem statement.

## 2. Test Cases

### Test Case 1: Standard Example

Input:
```text
image = [[1,1,1],[1,1,0],[1,0,1]], sr = 1, sc = 1, newColor = 2
```

Output:
```text
[[2,2,2],[2,2,0],[2,0,1]]
```

Explanation:
Starting at (1, 1) with color 1, all 4-directionally connected pixels with color 1 are changed to 2.

### Test Case 2: Same Color Edge Case

Input:
```text
image = [[0,0,0],[0,0,0]], sr = 0, sc = 0, newColor = 0
```

Output:
```text
[[0,0,0],[0,0,0]]
```

Explanation:
The starting pixel already has the new color, so the image remains unchanged.

### Test Case 3: Single Pixel Matrix

Input:
```text
image = [[5]], sr = 0, sc = 0, newColor = 9
```

Output:
```text
[[9]]
```

Explanation:
A 1x1 matrix correctly updates its single element.

## 3. AI-Generated Approach

### Approach: Depth-First Search

Perform a recursive Depth-First Search (DFS) starting from the given source cell, replacing all connected cells of the original color with the new color.

**Step-by-Step Reasoning:**
1. Check if the starting cell's color is already equal to the new color. If so, return the image immediately to prevent infinite recursion.
2. Store the initial color of the starting cell as the target old color.
3. Initiate a recursive DFS function from the starting cell, which checks boundaries, validates the color, updates the cell to the new color, and recursively visits all 4 adjacent directions.

**Why It Works:**
DFS systematically explores all 4-directionally connected components that share the initial color. By updating visited cells to the new color, it prevents cycles and guarantees that every connected pixel is recolored exactly once.

### Time Complexity

O(N * M)

### Space Complexity

O(N * M)

## 4. Java Solution

### Required Concepts

- Recursion
- Matrix Traversal
- Call Stack

### Original Accepted Submission

```java
class Solution {
    public int[][] floodFill(int[][] image, int sr, int sc, int newColor) {
        // code here
        int i=image.length;
        int j=image[0].length;
        
        if(image[sr][sc]==newColor)
        {
            return image;
        }
        
        int oldcolor=image[sr][sc];
        
        dfs(image,sr,sc,oldcolor,newColor);
        return image;
        
    }
    
    
    public static void dfs(int[][] img,int x,int y, int oldcolor,int newcolor)
    {
        if(x<0 || x>img.length-1 || y<0 || y>img[0].length-1 || img[x][y]!=oldcolor)
        return;
        
        img[x][y]=newcolor;
        
        dfs(img,x+1,y,oldcolor,newcolor);
        dfs(img,x-1,y,oldcolor,newcolor);
        dfs(img,x,y+1,oldcolor,newcolor);
        dfs(img,x,y-1,oldcolor,newcolor);
    }
}
```

### AI-Generated Java Alternative

```java
class Solution {
    public int[][] floodFill(int[][] image, int sr, int sc, int newColor) {
        if (image[sr][sc] == newColor) {
            return image;
        }
        int oldColor = image[sr][sc];
        dfs(image, sr, sc, oldColor, newColor);
        return image;
    }
    
    private void dfs(int[][] img, int x, int y, int oldColor, int newColor) {
        if (x < 0 || x >= img.length || y < 0 || y >= img[0].length || img[x][y] != oldColor) {
            return;
        }
        img[x][y] = newColor;
        dfs(img, x + 1, y, oldColor, newColor);
        dfs(img, x - 1, y, oldColor, newColor);
        dfs(img, x, y + 1, oldColor, newColor);
        dfs(img, x, y - 1, oldColor, newColor);
    }
}
```

## 5. Python Solution

### Required Concepts

- Recursion limit
- Grid traversal
- In-place updates

### AI-Generated Python Implementation

```python
class Solution:
    def floodFill(self, image: list[list[int]], sr: int, sc: int, newColor: int) -> list[list[int]]:
        old_color = image[sr][sc]
        if old_color == newColor:
            return image
        
        rows, cols = len(image), len(image[0])
        
        def dfs(r, c):
            if r < 0 or r >= rows or c < 0 or c >= cols or image[r][c] != old_color:
                return
            image[r][c] = newColor
            dfs(r + 1, c)
            dfs(r - 1, c)
            dfs(r, c + 1)
            dfs(r, c - 1)
            
        dfs(sr, sc)
        return image
```

## 6. C++ Solution

### Required Concepts

- Vectors
- References
- DFS Traversal

### AI-Generated C++ Implementation

```cpp
#include <vector>
using namespace std;

class Solution {
public:
    void dfs(vector<vector<int>>& img, int x, int y, int oldColor, int newColor) {
        if (x < 0 || x >= img.size() || y < 0 || y >= img[0].size() || img[x][y] != oldColor) {
            return;
        }
        img[x][y] = newColor;
        dfs(img, x + 1, y, oldColor, newColor);
        dfs(img, x - 1, y, oldColor, newColor);
        dfs(img, x, y + 1, oldColor, newColor);
        dfs(img, x, y - 1, oldColor, newColor);
    }

    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int newColor) {
        int oldColor = image[sr][sc];
        if (oldColor == newColor) {
            return image;
        }
        dfs(image, sr, sc, oldColor, newColor);
        return image;
    }
};
```

## 7. Rust Solution

### Required Concepts

- Mutability
- Ownership
- Matrix indexing

### AI-Generated Rust Implementation

```rust
impl Solution {
    pub fn flood_fill(mut image: Vec<Vec<i32>>, sr: i32, sc: i32, new_color: i32) -> Vec<Vec<i32>> {
        let old_color = image[sr as usize][sc as usize];
        if old_color == new_color {
            return image;
        }
        Self::dfs(&mut image, sr as usize, sc as usize, old_color, new_color);
        image
    }

    fn dfs(img: &mut Vec<Vec<i32>>, x: usize, y: usize, old_color: i32, new_color: i32) {
        if img[x][y] != old_color {
            return;
        }
        img[x][y] = new_color;
        
        if x > 0 {
            Self::dfs(img, x - 1, y, old_color, new_color);
        }
        if x + 1 < img.len() {
            Self::dfs(img, x + 1, y, old_color, new_color);
        }
        if y > 0 {
            Self::dfs(img, x, y - 1, old_color, new_color);
        }
        if y + 1 < img[0].len() {
            Self::dfs(img, x, y + 1, old_color, new_color);
        }
    }
}
```

## 8. Motivation

> "Patience and persistence are the quiet foundations upon which master architects build complex solutions."

<div align="center">

## Thank You 🚀

</div>
