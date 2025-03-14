[![](https://img.shields.io/github/stars/LeetCode-in-C/LeetCode-in-C?label=Stars&style=flat-square)](https://github.com/LeetCode-in-C/LeetCode-in-C)
[![](https://img.shields.io/github/forks/LeetCode-in-C/LeetCode-in-C?label=Fork%20me%20on%20GitHub%20&style=flat-square)](https://github.com/LeetCode-in-C/LeetCode-in-C/fork)

## 41\. First Missing Positive

Hard

Given an unsorted integer array `nums`, return the smallest missing positive integer.

You must implement an algorithm that runs in `O(n)` time and uses constant extra space.

**Example 1:**

**Input:** nums = [1,2,0]

**Output:** 3

**Explanation:** The numbers in the range [1,2] are all in the array.

**Example 2:**

**Input:** nums = [3,4,-1,1]

**Output:** 2

**Explanation:** 1 is in the array but 2 is missing.

**Example 3:**

**Input:** nums = [7,8,9,11,12]

**Output:** 1

**Explanation:** The smallest positive integer 1 is missing.

**Constraints:**

*   <code>1 <= nums.length <= 10<sup>5</sup></code>
*   <code>-2<sup>31</sup> <= nums[i] <= 2<sup>31</sup> - 1</code>

## Solution

```c
#include <stdio.h>

void dfs(int* nums, int numsSize, int val) {
    if (val <= 0 || val > numsSize || val == nums[val - 1]) {
        return;
    }
    int temp = nums[val - 1];
    nums[val - 1] = val;
    dfs(nums, numsSize, temp);
}

int firstMissingPositive(int* nums, int numsSize) {
    for (int i = 0; i < numsSize; i++) {
        if (nums[i] <= 0 || nums[i] > numsSize || nums[i] == i + 1) {
            continue;
        }
        dfs(nums, numsSize, nums[i]);
    }
    
    for (int i = 0; i < numsSize; i++) {
        if (nums[i] != i + 1) {
            return i + 1;
        }
    }
    return numsSize + 1;
}
```