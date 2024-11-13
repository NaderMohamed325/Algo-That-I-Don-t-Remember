
---

# Algorithms I Forget

## 1. **Maximum Subarray Sum (Kadane's Algorithm)**

This algorithm finds the maximum sum of a contiguous subarray within a one-dimensional vector of integers. It uses Kadane's Algorithm, which maintains a running sum and checks if each element improves the maximum found so far.

### Code
```cpp
class Solution {
public:
    int maxSubArray(vector<int> &nums) {
        long long int Max = INT32_MIN;
        long long int sum = 0;
        for (int num : nums) {
            sum += num;
            Max = max(Max, sum);
            sum = max(sum, 0LL);
        }
        return Max;
    }
};
```

### Explanation

1. **Initialize variables**:
   - `Max` stores the maximum sum found so far, initialized to a very small number (`INT32_MIN`).
   - `sum` keeps the running total of the current subarray being evaluated.

2. **Iterate through each number** in `nums`:
   - Add `num` to the current `sum`.
   - Update `Max` if the current `sum` is larger.
   - Reset `sum` to 0 if it becomes negative, as a negative running sum won't help in finding a maximum subarray.

3. **Return `Max`**: The result is the maximum sum of any contiguous subarray in `nums`.

---

## 2. **Dutch National Flag (DNF) Algorithm**

The **DNF Algorithm** sorts an array containing three distinct values (`0`, `1`, `2`) in-place. It partitions the array into three sections: all `0`s, `1`s, and `2`s.

### Problem
Given an array `nums` containing only the elements `0`, `1`, and `2`, sort the array in-place without using additional libraries or sorting functions.

### Code
```cpp
class Solution {
public:
    void sortColors(vector<int>& nums) {
        int low = 0, mid = 0, high = nums.size() - 1;

        while (mid <= high) {
            switch (nums[mid]) {
                case 0:
                    swap(nums[low++], nums[mid++]);
                    break;
                case 1:
                    mid++;
                    break;
                case 2:
                    swap(nums[mid], nums[high--]);
                    break;
            }
        }
    }
};
```

### Explanation

1. **Initialize pointers**:
   - `low`: Boundary for 0s.
   - `mid`: Traverses the array.
   - `high`: Boundary for 2s.

2. **Three-way partition**:
   - If `nums[mid] == 0`: Swap `nums[low]` and `nums[mid]`, then increment `low` and `mid`.
   - If `nums[mid] == 1`: Increment `mid`.
   - If `nums[mid] == 2`: Swap `nums[mid]` and `nums[high]`, then decrement `high`.

3. **Result**: All `0`s are at the start, `1`s in the middle, and `2`s at the end.

### Complexity
- **Time**: \(O(n)\), where \(n\) is the array size.
- **Space**: \(O(1)\), in-place sorting.

---

## 3. **Pascal's Triangle (Specific Row)**

This algorithm calculates the \(k\)-th row of Pascal's Triangle using a dynamic programming approach that avoids redundant computations.

### Code
```cpp
vector<int> Solution::getRow(int A) {
    vector<int> ans(A + 1, 1); // Initialize the row with 1s
    for (int i = 1; i < A; ++i) {
        ans[i] = (long long)ans[i - 1] * (A - i + 1) / i;
    }
    return ans;
}
```

### Explanation

1. **Initialization**:
   - Create a vector `ans` of size \(A + 1\), initialized to all 1s.

2. **Iterative calculation**:
   - Use the relation \( C(n, k) = \frac{C(n, k-1) \cdot (n-k+1)}{k} \) to compute each value iteratively.

3. **Return the result**:
   - The final vector `ans` contains all values in the \(A\)-th row of Pascal's Triangle.

### Complexity
- **Time**: \(O(A)\), as it calculates each value in the row once.
- **Space**: \(O(A)\), for the result vector.

### Example
For \(A = 4\):
- Input: `4`
- Output: `[1, 4, 6, 4, 1]`

---

