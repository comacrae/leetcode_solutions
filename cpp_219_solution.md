#[219. Contains Duplicate II](https://leetcode.com/problems/contains-duplicate-ii/description/)

#[My Solution](https://leetcode.com/problems/contains-duplicate-ii/solutions/3047146/c-solution/)

![image](https://user-images.githubusercontent.com/76566137/212415482-18e8cc09-ecfd-4e17-abb5-a7f374b7e471.png)

# Intuition
My intuition was to use a hashmap to to track the last observed index for a given number in the `nums` vector.

# Approach
<!-- Describe your approach to solving the problem. -->
I create an empty hashmap and iterate over the nums vector. If a number has NOT been encountered yet, I add a key-value pair to the hashmap where the key is the number and the value is the index where that number was encountered.

If the number HAS been encountered, get the value, i.e. the index where the value was last observed. If the difference between the current index $$j$$ and the last-observed index $$i$$ is less than or equal to $$k$$, I return true. Otherwise, I update the last-observed index to the current index ($$i:=j$$). If the entire for-loop is iterated over, then there are no duplicate values matching the given constraints, so we return false.
# Complexity
- Time complexity:
$$O(n)$$ because at worst case there are no duplicates and we iterate through the entire vector.

- Space complexity:
$$O(n)$$ because in worst case the entire vector consists of unique values and we add all of them to the hashmap.

# Code
```
class Solution {
public:
    bool containsNearbyDuplicate(vector<int>& nums, int k) {
        unordered_map<int,int> map;
        for(int i = 0; i < nums.size();i++){
            if(!map.count(nums[i])) { // if not in map yet add it
                map[nums[i]] = i;
            } else {
                if((i - map[nums[i]]) <= k)
                    return true;
                else
                    map[nums[i]] = i;
            }
        }
        return false;
    }
};
```
