

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
