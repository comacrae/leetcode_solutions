# [557. Reverse Words in a String III](https://leetcode.com/problems/reverse-words-in-a-string-iii/description/)

# [My Solution](https://leetcode.com/problems/reverse-words-in-a-string-iii/solutions/2972165/c-solution/)

![image](https://user-images.githubusercontent.com/76566137/210092397-ad6b9e3d-5bf3-4c5e-bd87-0a7a21cb50be.png)


# Intuition
This problem was much, much easier to accomplish than the reverse string II problem. Given my previous experience with that problem, I saw that all I had to do was go from the start of the word to the end of each word and use the built-in `reverse` function to reverse the words in place. 

# Approach
I set two counters `i` and `j` to the beginning of the string. Then I began a for loop for `j` which would terminate when `j` had reached the end of the string. At the beginning of the loop, I would set `i` equal to `j`. Then `j` would increment until it hit a space or the end of the string. At this point, I would call `reverse` starting at `i` (where `j` began, which was either at the beginning of the string or the beginning of a word) and `j` (where j ended).

# Complexity
- Time complexity:
$$O(n)$$ as we increment once through the string.

- Space complexity:
$$O(1)$$ as we perform all operations in place.

# Code
```
class Solution {
public:
    string reverseWords(string s) {
        int i = 0;
        int n = s.size();
        for(int j =0; j < n;j++){
            i = j;
            while(s[j]!= ' ' && j < n){
                j++;
            }
            reverse(s.begin() + i, s.begin() + j);
        }
        return s;
    }
};
```
