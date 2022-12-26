# [344. Reverse Strings](https://leetcode.com/problems/reverse-string/solutions/)

# [My Solution](https://leetcode.com/problems/reverse-string/solutions/2954810/344-reverse-strings-c-solution/)

![image](https://user-images.githubusercontent.com/76566137/209575100-b86fa822-a306-44df-8fbc-3003decdb986.png)

# Intuition
Literally use pointers to traverse the array from front -> back and back-> front simultaneously.

# Approach
Instead of using a built-in function, I wanted to review pointers, so I performed the operation with two pointers : one beginning at the start of s, and one at the end of s. I then used a temporary char `c` to store the value dereferenced at char pointer `i` and swapped accordingly.

# Complexity
- Time complexity:
$$O(n)$$ because we perform $$n/2$$ operations, where $$n$$ is the length of the string.

- Space complexity:
$$O(1)$$ because no auxilary data structures are created or used. 

# Code
```
class Solution {
public:
    void reverseString(vector<char>& s) {
        char * i = &s[0];
        char * j = &s[s.size() - 1];
        char tmp;
        while (i < j){
            tmp = *i;
            *i = *j;
            *j = tmp;
            i++;
            j--;
        }
    }
};
```
