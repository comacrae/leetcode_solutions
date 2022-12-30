# [Remove Duplicates From Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)

# [My Solution](https://leetcode.com/problems/remove-duplicates-from-sorted-array/solutions/2972408/c-solution/)

![image](https://user-images.githubusercontent.com/76566137/210097963-494530a6-e6bf-4ec4-9747-3f41d1cf09bd.png)


# Intuition
I knew I had to do something with trailing pointers, but after working it out on paper, it turned out to be easier than I thought.

# Approach
Because the array is already sorted in non-descending order, we just need two pointers, `i` and `j`. `j` will increment until it either hits just before the end of the array (`j < nums.size() -1` or it hits a value different than the one at `i`. At this point, if the value at `i` actually is different than `j`, `i` increments by one and assigns the value at `j` to `i`. This is repeated until `j` hits the one just before the end of the array. We need the `if` statement because we want to account for an array consisting of only one value repeated $$n$$ number of times.

# Complexity
- Time complexity:
$$O(n)$$ because we simply iterate through the array once.

- Space complexity:
$$O(1)$$ because all operations are done in place.

# Code
```
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int i = 0;
        int j = 0;
        int n = nums.size();
        while(j < n - 1){
            while(nums[j] == nums[i] && j < n- 1){
                j++;
            }
            if(nums[j] != nums[i]){
                i++;
                nums[i] = nums[j];
            }
        }
    return i + 1;
    }
};
```
