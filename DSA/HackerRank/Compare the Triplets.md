# Compare the Triplets

## 1. Problem Details

**Platform:** HackerRank

**Question Link:**
https://www.hackerrank.com/challenges/compare-the-triplets/problem

**Question Name:** Compare the Triplets

**Question Description:**

.MathJax_SVG_Display {text-align: center; margin: 1em 0em; position: relative; display: block!important; text-indent: 0; max-width: none; max-height: none; min-width: 0; min-height: 0; width: 100%}
.MathJax_SVG .MJX-monospace {font-family: monospace}
.MathJax_SVG .MJX-sans-serif {font-family: sans-serif}
.MathJax_SVG {display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 100%; font-size-adjust: none; text-indent: 0; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0; min-height: 0; border: 0; padding: 0; margin: 0}
.MathJax_SVG * {transition: none; -webkit-transition: none; -moz-transition: none; -ms-transition: none; -o-transition: none}
.mjx-svg-href {fill: blue; stroke: blue}
.MathJax_SVG_LineBox {display: table!important}
.MathJax_SVG_LineBox span {display: table-cell!important; width: 10000em!important; min-width: 0; max-width: none; padding: 0; border: 0; margin: 0}
Alice and Bob each created one problem for HackerRank. A reviewer rates the two challenges, awarding points on a scale from 1 to 100 for three categories: problem clarity, originality, and difficulty. 



The rating for Alice's challenge is the triplet a = (a[0], a[1], a[2]), and the rating for Bob's challenge is the triplet b = (b[0], b[1], b[2]).



The task is to calculate their comparison points by comparing each category:    




•  If a[i] > b[i], then Alice is awarded 1 point. 
•  If a[i] < b[i], then Bob is awarded 1 point. 
•  If a[i] = b[i], then neither person receives a point.


Example   



a = [1, 2, 3] 

b = [3, 2, 1] 

  




• For elements *0*, Bob is awarded a point because a[0] < b[0].  
• For the equal elements a[1] and b[1], no points are earned.  
• Finally, for elements 2, a[2] > b[2] so Alice receives a point.  


The return array is [1, 1] with Alice's score first and Bob's second.  



Function Description  



Complete the function compareTriplets with the following parameter(s):  




• int a[3]: Alice's challenge rating  
• int b[3]: Bob's challenge rating   


Returns  




• int[2]: the first element is Alice's score and the second is Bob's score
Input Format

.MathJax_SVG_Display {text-align: center; margin: 1em 0em; position: relative; display: block!important; text-indent: 0; max-width: none; max-height: none; min-width: 0; min-height: 0; width: 100%}
.MathJax_SVG .MJX-monospace {font-family: monospace}
.MathJax_SVG .MJX-sans-serif {font-family: sans-serif}
.MathJax_SVG {display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 100%; font-size-adjust: none; text-indent: 0; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0; min-height: 0; border: 0; padding: 0; margin: 0}
.MathJax_SVG * {transition: none; -webkit-transition: none; -moz-transition: none; -ms-transition: none; -o-transition: none}
.mjx-svg-href {fill: blue; stroke: blue}
.MathJax_SVG_LineBox {display: table!important}
.MathJax_SVG_LineBox span {display: table-cell!important; width: 10000em!important; min-width: 0; max-width: none; padding: 0; border: 0; margin: 0}
The first line contains 3 space-separated integers, a[0], a[1], and a[2], the respective values in triplet a. 

The second line contains 3 space-separated integers, b[0], b[1], and b[2], the respective values in triplet b.

Constraints

.MathJax_SVG_Display {text-align: center; margin: 1em 0em; position: relative; display: block!important; text-indent: 0; max-width: none; max-height: none; min-width: 0; min-height: 0; width: 100%}
.MathJax_SVG .MJX-monospace {font-family: monospace}
.MathJax_SVG .MJX-sans-serif {font-family: sans-serif}
.MathJax_SVG {display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 100%; font-size-adjust: none; text-indent: 0; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0; min-height: 0; border: 0; padding: 0; margin: 0}
.MathJax_SVG * {transition: none; -webkit-transition: none; -moz-transition: none; -ms-transition: none; -o-transition: none}
.mjx-svg-href {fill: blue; stroke: blue}
.MathJax_SVG_LineBox {display: table!important}
.MathJax_SVG_LineBox span {display: table-cell!important; width: 10000em!important; min-width: 0; max-width: none; padding: 0; border: 0; margin: 0}

•  1 ≤ a[i] ≤ 100
•  1 ≤ b[i] ≤ 100
Sample Input 0

.MathJax_SVG_Display {text-align: center; margin: 1em 0em; position: relative; display: block!important; text-indent: 0; max-width: none; max-height: none; min-width: 0; min-height: 0; width: 100%}
.MathJax_SVG .MJX-monospace {font-family: monospace}
.MathJax_SVG .MJX-sans-serif {font-family: sans-serif}
.MathJax_SVG {display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 100%; font-size-adjust: none; text-indent: 0; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0; min-height: 0; border: 0; padding: 0; margin: 0}
.MathJax_SVG * {transition: none; -webkit-transition: none; -moz-transition: none; -ms-transition: none; -o-transition: none}
.mjx-svg-href {fill: blue; stroke: blue}
.MathJax_SVG_LineBox {display: table!important}
.MathJax_SVG_LineBox span {display: table-cell!important; width: 10000em!important; min-width: 0; max-width: none; padding: 0; border: 0; margin: 0}
5 6 7
3 6 10

Sample Output 0

.MathJax_SVG_Display {text-align: center; margin: 1em 0em; position: relative; display: block!important; text-indent: 0; max-width: none; max-height: none; min-width: 0; min-height: 0; width: 100%}
.MathJax_SVG .MJX-monospace {font-family: monospace}
.MathJax_SVG .MJX-sans-serif {font-family: sans-serif}
.MathJax_SVG {display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 100%; font-size-adjust: none; text-indent: 0; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0; min-height: 0; border: 0; padding: 0; margin: 0}
.MathJax_SVG * {transition: none; -webkit-transition: none; -moz-transition: none; -ms-transition: none; -o-transition: none}
.mjx-svg-href {fill: blue; stroke: blue}
1 1

Explanation 0

.MathJax_SVG_Display {text-align: center; margin: 1em 0em; position: relative; display: block!important; text-indent: 0; max-width: none; max-height: none; min-width: 0; min-height: 0; width: 100%}
.MathJax_SVG .MJX-monospace {font-family: monospace}
.MathJax_SVG .MJX-sans-serif {font-family: sans-serif}
.MathJax_SVG {display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 100%; font-size-adjust: none; text-indent: 0; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0; min-height: 0; border: 0; padding: 0; margin: 0}
.MathJax_SVG * {transition: none; -webkit-transition: none; -moz-transition: none; -ms-transition: none; -o-transition: none}
.mjx-svg-href {fill: blue; stroke: blue}
.MathJax_SVG_LineBox {display: table!important}
.MathJax_SVG_LineBox span {display: table-cell!important; width: 10000em!important; min-width: 0; max-width: none; padding: 0; border: 0; margin: 0}
In this example: 




• 
• 


Now, let's compare each individual score:




• , so Alice receives  point.
• , so nobody receives a point.
• , so Bob receives  point.


Alice's comparison score is , and Bob's comparison score is . Thus, we return the array .  

Sample Input 1

.MathJax_SVG_Display {text-align: center; margin: 1em 0em; position: relative; display: block!important; text-indent: 0; max-width: none; max-height: none; min-width: 0; min-height: 0; width: 100%}
.MathJax_SVG .MJX-monospace {font-family: monospace}
.MathJax_SVG .MJX-sans-serif {font-family: sans-serif}
.MathJax_SVG {display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 100%; font-size-adjust: none; text-indent: 0; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0; min-height: 0; border: 0; padding: 0; margin: 0}
.MathJax_SVG * {transition: none; -webkit-transition: none; -moz-transition: none; -ms-transition: none; -o-transition: none}
.mjx-svg-href {fill: blue; stroke: blue}
.MathJax_SVG_LineBox {display: table!important}
.MathJax_SVG_LineBox span {display: table-cell!important; width: 10000em!important; min-width: 0; max-width: none; padding: 0; border: 0; margin: 0}
17 28 30
99 16 8

Sample Output 1

.MathJax_SVG_Display {text-align: center; margin: 1em 0em; position: relative; display: block!important; text-indent: 0; max-width: none; max-height: none; min-width: 0; min-height: 0; width: 100%}
.MathJax_SVG .MJX-monospace {font-family: monospace}
.MathJax_SVG .MJX-sans-serif {font-family: sans-serif}
.MathJax_SVG {display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 100%; font-size-adjust: none; text-indent: 0; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0; min-height: 0; border: 0; padding: 0; margin: 0}
.MathJax_SVG * {transition: none; -webkit-transition: none; -moz-transition: none; -ms-transition: none; -o-transition: none}
.mjx-svg-href {fill: blue; stroke: blue}
2 1

Explanation 1

.MathJax_SVG_Display {text-align: center; margin: 1em 0em; position: relative; display: block!important; text-indent: 0; max-width: none; max-height: none; min-width: 0; min-height: 0; width: 100%}
.MathJax_SVG .MJX-monospace {font-family: monospace}
.MathJax_SVG .MJX-sans-serif {font-family: sans-serif}
.MathJax_SVG {display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 100%; font-size-adjust: none; text-indent: 0; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0; min-height: 0; border: 0; padding: 0; margin: 0}
.MathJax_SVG * {transition: none; -webkit-transition: none; -moz-transition: none; -ms-transition: none; -o-transition: none}
.mjx-svg-href {fill: blue; stroke: blue}
.MathJax_SVG_LineBox {display: table!important}
.MathJax_SVG_LineBox span {display: table-cell!important; width: 10000em!important; min-width: 0; max-width: none; padding: 0; border: 0; margin: 0}
Comparing the  elements,  so Bob receives a point. 

Comparing the  and  elements,  and  so Alice receives two points. 

The return array is .

## 2. Test Cases

### Test Case 1: Standard Mixed Comparisons

Input:
```text
a = [5, 6, 7], b = [3, 6, 10]
```

Output:
```text
[1, 1]
```

Explanation:
For index 0, 5 > 3 so Alice gets 1 point. For index 1, 6 == 6 so no points are awarded. For index 2, 7 < 10 so Bob gets 1 point. Final score is [1, 1].

### Test Case 2: One Sided Sweep

Input:
```text
a = [17, 28, 30], b = [99, 16, 8]
```

Output:
```text
[2, 1]
```

Explanation:
Alice loses the first category (17 < 99) giving Bob 1 point, but wins the remaining two (28 > 16, 30 > 8) giving Alice 2 points. Final score is [2, 1].

### Test Case 3: All Ties

Input:
```text
a = [100, 100, 100], b = [100, 100, 100]
```

Output:
```text
[0, 0]
```

Explanation:
All elements at each corresponding index are equal, so neither participant receives any points.

## 3. AI-Generated Approach

### Approach: Linear Traversal / Simulation

Iterate through each category index from 0 to 2, comparing the corresponding rating values of Alice and Bob. Increment Alice's score if her score is strictly greater, increment Bob's score if Bob's score is strictly greater, and do nothing if they are equal.

**Step-by-Step Reasoning:**
1. Initialize two counters, aliceScore and bobScore, to 0.
2. Iterate over index i from 0 to 2.
3. If a[i] > b[i], increment aliceScore by 1.
4. Else if a[i] < b[i], increment bobScore by 1.
5. After the loop finishes, return the results as a two-element array or list [aliceScore, bobScore].

**Why It Works:**
Each category evaluation is completely independent. A single pass over the 3 fixed elements directly simulates the rules provided in the problem statement.

### Time Complexity

O(1)

### Space Complexity

O(1)

## 4. Java Solution

### Required Concepts

- List vs Array
- Comparison Operators
- Autoboxing

### Original Accepted Submission

```java
List<Integer> a = Stream.of(bufferedReader.readLine().replaceAll("\\s+$", 
        "").split(" "))
            .map(Integer::parseInt)
            .collect(toList());
        getenv("OUTPUT_PATH")));
        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.
        (System.in));
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader
    public static void main(String[] args) throws IOException {
public class Solution {

}

        return ans;
    }
        ans.add(alice);
        }
            }
                bob++;
            {
            else if(a.get(i)<b.get(i))
            }
                alice++;
        ans.add(bob);
```

### AI-Generated Java Alternative

```java
import java.util.Arrays;
import java.util.List;

public class Solution {
    public static List<Integer> compareTriplets(List<Integer> a, List<Integer> b) {
        int aliceScore = 0;
        int bobScore = 0;

        for (int i = 0; i < 3; i++) {
            if (a.get(i) > b.get(i)) {
                aliceScore++;
            } else if (a.get(i) < b.get(i)) {
                bobScore++;
            }
        }

        return Arrays.asList(aliceScore, bobScore);
    }
}
```

## 5. Python Solution

### Required Concepts

- zip() iterator
- Tuple unpacking
- List literals

### AI-Generated Python Implementation

```python
def compareTriplets(a, b):
    alice_score = 0
    bob_score = 0
    
    for x, y in zip(a, b):
        if x > y:
            alice_score += 1
        elif x < y:
            bob_score += 1
            
    return [alice_score, bob_score]
```

## 6. C++ Solution

### Required Concepts

- std::vector
- Direct element indexing
- O(1) auxiliary space

### AI-Generated C++ Implementation

```cpp
#include <vector>

std::vector<int> compareTriplets(const std::vector<int>& a, const std::vector<int>& b) {
    int aliceScore = 0;
    int bobScore = 0;

    for (int i = 0; i < 3; ++i) {
        if (a[i] > b[i]) {
            aliceScore++;
        } else if (a[i] < b[i]) {
            bobScore++;
        }
    }

    return {aliceScore, bobScore};
}
```

## 7. Rust Solution

### Required Concepts

- Pattern Matching / Ordering
- Iterators and zip
- Ownership & Borrowing

### AI-Generated Rust Implementation

```rust
pub fn compare_triplets(a: &[i32], b: &[i32]) -> Vec<i32> {
    let mut alice_score = 0;
    let mut bob_score = 0;

    for i in 0..3 {
        if a[i] > b[i] {
            alice_score += 1;
        } else if a[i] < b[i] {
            bob_score += 1;
        }
    }

    vec![alice_score, bob_score]
}
```

## 8. Motivation

> "Mastery begins with executing the simplest logic with flawless clarity and elegance."

<div align="center">

## Thank You 🚀

</div>
