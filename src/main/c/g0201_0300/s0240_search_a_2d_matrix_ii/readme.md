[![](https://img.shields.io/github/stars/LeetCode-in-C/LeetCode-in-C?label=Stars&style=flat-square)](https://github.com/LeetCode-in-C/LeetCode-in-C)
[![](https://img.shields.io/github/forks/LeetCode-in-C/LeetCode-in-C?label=Fork%20me%20on%20GitHub%20&style=flat-square)](https://github.com/LeetCode-in-C/LeetCode-in-C/fork)

## 240\. Search a 2D Matrix II

Medium

Write an efficient algorithm that searches for a value `target` in an `m x n` integer matrix `matrix`. This matrix has the following properties:

*   Integers in each row are sorted in ascending from left to right.
*   Integers in each column are sorted in ascending from top to bottom.

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/11/24/searchgrid2.jpg)

**Input:** matrix = \[\[1,4,7,11,15],[2,5,8,12,19],[3,6,9,16,22],[10,13,14,17,24],[18,21,23,26,30]], target = 5

**Output:** true

**Example 2:**

![](https://assets.leetcode.com/uploads/2020/11/24/searchgrid.jpg)

**Input:** matrix = \[\[1,4,7,11,15],[2,5,8,12,19],[3,6,9,16,22],[10,13,14,17,24],[18,21,23,26,30]], target = 20

**Output:** false

**Constraints:**

*   `m == matrix.length`
*   `n == matrix[i].length`
*   `1 <= n, m <= 300`
*   <code>-10<sup>9</sup> <= matrix[i][j] <= 10<sup>9</sup></code>
*   All the integers in each row are **sorted** in ascending order.
*   All the integers in each column are **sorted** in ascending order.
*   <code>-10<sup>9</sup> <= target <= 10<sup>9</sup></code>

## Solution

```c
#include <stdbool.h>
#include <stdio.h>

bool searchMatrix(int** matrix, int matrixSize, int* matrixColSize, int target) {
    int r = 0;
    int c = matrixColSize[0] - 1; // Start from the top-right corner

    while (r < matrixSize && c >= 0) {
        if (matrix[r][c] == target) {
            return true;
        } else if (matrix[r][c] > target) {
            c--; // Move left
        } else {
            r++; // Move down
        }
    }
    return false;
}
```