# [136. Single Number](https://leetcode.com/problems/single-number/description/)

#[My Solution](https://leetcode.com/problems/single-number/solutions/2994182/c-suboptimal-solution-using-two-hashsets/)

![image](https://user-images.githubusercontent.com/76566137/210432801-de293d6c-9108-4abb-a592-7783650252ca.png)

# Intuition
The restrictions of linear time complexity and constance space complexity made this problem seem initially difficult, so I'm glad that I thought of a solution without any hints or help (although it's far from optimal).

# Approach
I first create two unordered sets, `set1` and `set2`. Both are of constant length 15000 because this is equal to the max range of `nums` divided by 2:

$$(3 * 10 ^ 4 )/2 = 15000$$

I chose this value because this is the minimum amount of a hashset required to ensure a collision occurs only when the *exact same* value is encountered in `nums`. 

I then iterate through the input array, adding each value to `set1` (the first hashset). For each value, if the add is failed (meaning there is a collision, which by the previous restriction of the set size, means that this value is a true duplicate) I add this value to the second hash set. 

Once the input array is iterated through the second hash set will *only* contain values which were duplicated. Then I just iterate through the input array one more time and attempt to insert values into this second hash set. The first element that is successfully inserted is the only value which wasn't a duplicate.

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$$O(n)$$ because I iterate through the array twice -> $2n$ values processed. 
- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$$O(1)$$ because the hashsets are of constant size regardless of the size of the input array.

# Code
```
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        unordered_set<int> set1(15000);
        unordered_set<int> set2(15000);
        for(int n : nums){
            if(!set1.insert(n).second) // only insert to set2 if there's a collision
                set2.insert(n); 
        }
        // now set2 only contains duplicates
        int i = 0;
        while(!set2.insert(nums[i]).second){
            i++;
        }
        return nums[i];
    }
};
```
