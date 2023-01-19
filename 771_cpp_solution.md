# [771. Jewels & Stones](https://leetcode.com/problems/jewels-and-stones/description/)

# [My Solution](https://leetcode.com/problems/jewels-and-stones/solutions/3074499/c-solution/)


# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Use a hashset to keep track of jewel chars and record collisions in jewel hashset for each stone char
# Approach
<!-- Describe your approach to solving the problem. -->
I create a hashset to represent the unique characters in the jewel string. I then iterate over the stones string and for each "stone" char that collides in the jewel hashset, I increase a counter that represents the number of stones encountered so far. This counter is then returned a the number of jewels in the stone string.
# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$$O(max(m,n))$$ where $$m$ and $$n$$ are the lengths of the jewel and stone strings respectively, as we iterate over both strings and an $$O(1)$$ lookup or insert is performed for each char. 

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$$O(m)$$ where $$m$$ is the length of the jewels string.
# Code
```
class Solution {
public:
    int numJewelsInStones(string jewels, string stones) {
        unordered_set<char> jewelSet;
        int count = 0;
        for(int i = 0; i < jewels.size(); i++){
            jewelSet.insert(jewels[i]);
        }
        for(int i = 0; i < stones.size(); i++){
            if(jewelSet.count(stones[i])){
                count++;
            }
        }
        return count;
    }
};
```
