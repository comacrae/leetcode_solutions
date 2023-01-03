# [217. Contains Duplicate](https://leetcode.com/problems/contains-duplicate/description/)

# [My Solution](https://leetcode.com/problems/contains-duplicate/post-solution/)

![image](https://user-images.githubusercontent.com/76566137/210282944-bfdd8f4b-6567-400d-b74b-3425699af4ee.png)

# Intuition
My intution was to use a hashset to keep track of values that had been encountered. Since only unique values can be contained with a hashset (aka  `unordered_set` in C++), the fact that a value was already in the hashset when it was encountered was evidence of a duplicate existing.

# Approach
I iterate through the values and check if they are already present in the hashset. If they are present, then they are a duplicate, so I return `true` to indicate that a duplicate exists. Otherwise I add the value to the hashset and go to the next value to check. If all values in the vector have been checked, then no duplicates were encountered. In that case, I return `false` to indicate that there are no duplicates in the hashset.

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
According to the [C++ docs](https://cplusplus.com/reference/unordered_set/unordered_set/insert/), the `unordered_set` class' `insert` method has $$O(n)$$ time complexity, so the time complexity is $$O(n^2)$$ ($$n$$ steps $$n$$ times), but given the nature of hashing, the average is closer to $$O(n)$$.
- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$$O(n)$$ for creating the hashset. 
# Code
```
class Solution {
public:
    bool containsDuplicate(vector<int>& nums){
        unordered_set<int> set;
        for(int num: nums){
            if(!set.insert(num).second) return true;
        }
        return false;
    }
};
```
