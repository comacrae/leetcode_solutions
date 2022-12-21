# 747. Largest Number of at least Twice the Others
![image](https://user-images.githubusercontent.com/76566137/208920161-c7beeeb6-9dc1-4898-835b-d8ad52e5c7fe.png)


## [Link To Description](https://leetcode.com/problems/largest-number-at-least-twice-of-others/description/)
## [Link To My Solution](https://leetcode.com/problems/largest-number-at-least-twice-of-others/solutions/2881390/747-largest-number-at-least-twice-of-others-solution-c/)
# Intuition
My initial thought for solving this problem was I would want to find the max of the array. I also thought that I would have to iterate through the array twice, since I would have to do it once to find the max, and then once to make sure the other values didn't break the "at least twice" condition. I'm sure there's a way that I could have checked both conditions on the go (in the first loop) by having two max indexers; one for the double maxer and one for the potential return value index. But this is my initial solution, so this is what I will write up.
# Approach
I looped through the array once to find the max, then looped through it a second time to make sure all values satisfied the "at least twice" condition.

# Complexity
- Time complexity:
Time complexity is $$O(n)$$ because we have to loop through all values twice ($$n$$ for the first loop plus $$n$$ for the second loop leading to 2n which leads to just $$O(n)$$)

- Space complexity:
Space complexity is $$O(1)$$ as we never create any copies of the array; just some variables (four to be precise).

# Code
```
class Solution {
public:
    int dominantIndex(vector<int>& nums) {
        int argmax = 0;
        int len = nums.size();
        for(int i = 0; i < len;i++){
            if (nums[i] > nums[argmax])
                argmax = i;
        }
        int i =0;
        int val = nums[argmax];
        while (i < len){
            if ((i != argmax) && (val < (nums[i] * 2)))
                return -1;
            i++;
        }
        return argmax;
    }
};
```
