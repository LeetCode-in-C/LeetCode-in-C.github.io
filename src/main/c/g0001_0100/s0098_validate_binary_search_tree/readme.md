[![](https://img.shields.io/github/stars/LeetCode-in-C/LeetCode-in-C?label=Stars&style=flat-square)](https://github.com/LeetCode-in-C/LeetCode-in-C)
[![](https://img.shields.io/github/forks/LeetCode-in-C/LeetCode-in-C?label=Fork%20me%20on%20GitHub%20&style=flat-square)](https://github.com/LeetCode-in-C/LeetCode-in-C/fork)

## 98\. Validate Binary Search Tree

Medium

Given the `root` of a binary tree, _determine if it is a valid binary search tree (BST)_.

A **valid BST** is defined as follows:

*   The left subtree of a node contains only nodes with keys **less than** the node's key.
*   The right subtree of a node contains only nodes with keys **greater than** the node's key.
*   Both the left and right subtrees must also be binary search trees.

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/12/01/tree1.jpg)

**Input:** root = [2,1,3]

**Output:** true

**Example 2:**

![](https://assets.leetcode.com/uploads/2020/12/01/tree2.jpg)

**Input:** root = [5,1,4,null,null,3,6]

**Output:** false

**Explanation:** The root node's value is 5 but its right child's value is 4.

**Constraints:**

*   The number of nodes in the tree is in the range <code>[1, 10<sup>4</sup>]</code>.
*   <code>-2<sup>31</sup> <= Node.val <= 2<sup>31</sup> - 1</code>

## Solution

```c
#include <stdio.h>
#include <stdbool.h>
#include <limits.h>

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     struct TreeNode *left;
 *     struct TreeNode *right;
 * };
 */
// Helper function to check if the tree is a valid BST
bool solve(struct TreeNode* root, long left, long right) {
    if (root == NULL) {
        return true;
    }
    if (root->val <= left || root->val >= right) {
        return false;
    }
    return solve(root->left, left, root->val) && solve(root->right, root->val, right);
}

// Main function to check if a tree is a valid BST
bool isValidBST(struct TreeNode* root) {
    return solve(root, LONG_MIN, LONG_MAX);
}
```