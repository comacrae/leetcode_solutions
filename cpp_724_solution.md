# 724. Find Pivot Index

## [Link to Problem Description](https://leetcode.com/problems/find-pivot-index/description/)

## [Link to my Solution](https://leetcode.com/problems/find-pivot-index/solutions/2881339/724-find-pivot-index-solution-c/)
# Intuition

My first attempt was a brute force one where I looped over all values of the vector, using each as a pivot; For each pivot, I summed up the values to the left or right of the pivot and then compared them (while keeping in mind the edge cases where pivot is num[0] or num[size-1]). While this worked , it was extremely slow and didn't pass the LeetCode time limit. 

# Approach
I used the first hint which suggested I build a leftSum array. I realized that instead of building an array, I could have a value which tracks the left sum and a value which tracks the right sum; as the pivot crawled forward one index at at time, I could subtract the pivot's value from the right sum and add the pivot's value to the left sum. My approach is slightly more verbose than necessary; I will return in the future to update the code with a more efficient solution.

# Complexity
- Time complexity:
$$O(n)$$ because it takes n steps to generate sum, then n steps to step through each pivot until end of int vector is reached.

- Space complexity:

O(1) because no additional data structures are created; Regardless of num vector size, we will use three ints (pivot, l_sum, and r_sum) to identify pivot.

# Code
```
class Solution {
public:
    int pivotIndex(vector<int>& nums) {
        int pivot = 0;
        int l_sum = 0;
        int r_sum = 0;
        int len = nums.size();
        for(int i=1; i< len;i++){
            r_sum += nums[i];
        }

        while(pivot < len - 1){
            if (l_sum == r_sum){
                return pivot;
            }
            else {
                l_sum += nums[pivot];
                pivot++;
                r_sum -= nums[pivot];
            }
        }
        r_sum = 0;
        if (l_sum == r_sum) {
            return pivot;
        } else  { 
            return -1;
        }


    }
};
```
