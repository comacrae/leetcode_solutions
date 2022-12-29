# [189. Rotate Array](https://leetcode.com/problems/rotate-array/description/)

# [Solution](https://leetcode.com/problems/rotate-array/solutions/2965459/c-solution/)

![image](https://user-images.githubusercontent.com/76566137/209901763-5225827e-9177-482e-a934-934b265a5f75.png)


# Intuition
My intution was to use the modulo operator and try to do it in place, but I eventually settled with creating a copy and decided to figure out the O(1) space complexity solution later.
# Approach
If $$k$$ is the number of "rotates" and $$n$$ is the length of the `nums` array, we only really need to do at most $$k \% n$$ operations. With this in mind, there is a pattern; given a starting index $$i$$, the final index $$j$$ can be determined using the following formula:

$$j = (i + k) \% n $$


Using this formula, I first created a temporary "placeholder" array initialized with zeroes named `tmp`. I then iterated through the `nums` array, assigning each $$i$$th from `nums` to the appropriate $$j$$th index in the `tmp` array. I then assigned `tmp` to `nums`.
# Complexity
- Time complexity:
$$O(n)$$ because we iterate through the entire nums array in the worst case scenario (where $$k\%n = n-1$$).

- Space complexity:
$$O(n)$$ because we create a copy array of size $$n$$.

# Code
```
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        k = k % nums.size();
        vector<int> tmp(nums.size(),0);
        for(int i =0; i < nums.size(); i++){
            tmp[(k + i)% nums.size()] = nums[i];
        }
        nums = tmp;
    }
};
```
