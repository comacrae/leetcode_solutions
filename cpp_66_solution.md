# 66. Plus One
![image](https://user-images.githubusercontent.com/76566137/208919290-63d05326-0bf7-4ac0-b7ea-beb9d66e8d9c.png)

## [Link to Problem Description](https://leetcode.com/problems/plus-one/description/)
## [Link to my Solution](https://leetcode.com/problems/plus-one/solutions/2926698/plus-one-c-solution/)

# Intuition
I knew I had to start at the end of the number array and increment in the fashion that we were taught to sum large numbers in elementary school (stacking two or more numbers on top of eachother, adding, and then carrying the 1, etc). I also initially thought that I had to account for the scenario where there was just a single number in the array, but this turned out to be false.

# Approach
My initial approach was too complex. I started getting lost in else-if branches and I realized I didn't have to account for how many values there were in the array. I just had to add to the terminal value and carry through if it was 10 or greater.

# Complexity
- Time complexity:
- Time complexity is O(n) because in the worse case we have to traverse through the entire array, incrementing each value by one (and then adding a new value: for example, 9999 -> 10000).

- Space complexity:
Space complexity is O(n) because in the worst case scenario, we expand the array by one.

# Code
```
class Solution {
public:
    vector<int> plusOne(vector<int>& digits) {
        int len = digits.size();
        int idx = len - 1;
        digits[idx] += 1;
        while (idx > 0) {
            if (digits[idx] > 9) {
                digits[idx] = 0;
                digits[idx - 1] += 1;
            }
            idx--;
        }
        if (digits[idx] > 9) {
            digits[idx] = 1;
            digits.push_back(0);
        }
    return digits;
    }
};
```
