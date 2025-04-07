Below are several variants of the contiguous subsequence (maximum subarray) problem, each with increasing levels of difficulty or different constraints:

----------

### 1. Basic Variant (Standard Maximum Subarray)

**Problem:**  
Given an array of integers, find the contiguous subarray (non-empty) with the maximum sum.  
**Difficulty:** Easy  
**Hint:** Use the modified Kadane’s algorithm that initializes with the first element.

----------

### 2. Maximum Subarray with Allowed Empty Subarray

**Problem:**  
Given an array of integers, find the contiguous subarray (which may be empty) with the maximum sum.  
**Difficulty:** Easy  
**Hint:** Modify Kadane’s algorithm to allow the sum to reset to 0; this way, if all numbers are negative, the result is 0 (empty subsequence).

----------

### 3. Maximum Subarray with a Twist (At Most k Elements)

**Problem:**  
Given an array of integers and an integer k, find the contiguous subarray with at most k elements that has the maximum sum.  
**Difficulty:** Medium  
**Hint:** You may need to maintain a sliding window of size up to k and explore dynamic programming approaches or two-pointer techniques.

----------

### 4. Maximum Subarray Product

**Problem:**  
Given an array of integers, find the contiguous subarray (non-empty) whose product is maximum.  
**Difficulty:** Medium  
**Hint:** The presence of negative numbers means you have to track both the maximum and minimum products up to the current index.

----------

### 5. Maximum Average Subarray

**Problem:**  
Given an array of integers and an integer k, find the contiguous subarray of length at least k that has the maximum average value.  
**Difficulty:** Medium to Hard  
**Hint:** Binary search on the answer combined with a prefix sum transformation can be an effective strategy.

----------

### 6. Maximum Subarray Sum in a 2D Array (Matrix)

**Problem:**  
Given a 2D matrix of integers, find the submatrix (formed by contiguous rows and columns) with the maximum sum.  
**Difficulty:** Hard  
**Hint:** A common approach is to fix two rows, collapse the 2D problem into a 1D maximum subarray problem, and then iterate over all row pairs.

----------

### 7. Maximum Subarray Sum in a 3D Array

**Problem:**  
Given a 3D matrix of integers, find the submatrix (formed by contiguous rows and columns) with the maximum sum.  
**Difficulty:** Hard  
**Hint:** A common approach is to fix two rows, collapse the 2D problem into a 1D maximum subarray problem, and then iterate over all row pairs.

----------

### 7. Maximum Non-Contiguous Subsequence Sum

**Problem:**  
Given an array of integers, find the subsequence (not necessarily contiguous) with the maximum sum.  
**Difficulty:** Easy to Medium  
**Hint:** This variant is simpler since you typically add all positive numbers. The twist is if the array contains only negatives, you return the maximum (least negative) element.

----------

### 8. Online Maximum Subarray (Streaming)

**Problem:**  
Design an algorithm that processes an infinite stream of numbers and at any moment can output the maximum sum of a contiguous subsequence seen so far.  
**Difficulty:** Hard  
**Hint:** This variant challenges you to update your result without storing the entire stream; consider using online or incremental algorithms with limited memory.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA3MTc5NTcxOF19
-->