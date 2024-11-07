

# Algorithms I Forget

## Maximum Subarray Sum (Kadane's Algorithm)

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
            Max = max({Max, sum});
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
   - If `sum` becomes negative, reset it to 0, as any negative sum would not help in finding a maximum subarray.

3. **Return `Max`**: The result is the maximum sum of any contiguous subarray in `nums`.





## The **DNF  Algorithm** is used to sort an array containing three distinct values .


### Problem
Given an array `nums` containing only the elements `0`, `1`, and `2`, sort the array in-place without using any additional libraries or sorting functions.

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
   - `low`: points to the boundary of 0s.
   - `mid`: traverses through the array.
   - `high`: points to the boundary of 2s.

2. **Three-way partition**:
   - If `nums[mid] == 0`, swap `nums[low]` and `nums[mid]`, then increment both `low` and `mid`.
   - If `nums[mid] == 1`, increment `mid`.
   - If `nums[mid] == 2`, swap `nums[mid]` and `nums[high]`, then decrement `high`.

3. **Result**: By the end, all `0`s are at the beginning, `1`s are in the middle, and `2`s are at the end of the array.

### Complexity
- **Time Complexity**: \(O(n)\), where \(n\) is the size of the array.
- **Space Complexity**: \(O(1)\), as it sorts in-place.
```

This is a widely used algorithm, especially in sorting and array manipulation problems, where you need a linear-time solution for a limited set of values.
