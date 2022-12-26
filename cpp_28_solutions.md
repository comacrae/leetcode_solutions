# [28. Find the Index of the First Occurrence in a String](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/description/)

# [My Solution](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/solutions/2951804/c-find-the-index-of-the-first-occurrence-in-a-string/)

![image](https://user-images.githubusercontent.com/76566137/209495234-d0b5f600-e9f3-4922-985a-560dec2520b1.png)

# Intuition
My intution was to do something with dynamic programming but I lack the knowledge to approach it that way at the moment. So what I did instead was a bruteforce approach.
# Approach
I traverse the string until I find the first matching letter, then compare to see if the last letter is present; then I check to make sure all letters appear and if so, I return the first index where the substring appeared. If the end of the string is reached, there are no matches so I return -1.
# Complexity
- Time complexity:
Time complexity is $$O(n^2)$$ because in the worst case, almost the entirety of the haystack is searched repeatedly for the word and there is only a single letter invalid.
- Space complexity:
$$O(1)$$ no extra memory is allocated beyond a constant number of variables for keeping tracks of indices.
# Code
```
class Solution {
public:
    int strStr(string haystack, string needle) {
        int i = 0;
        while(i + needle.size() - 1 < haystack.size()){
            if(haystack[i] == needle[0] && haystack[i + needle.size() - 1] == needle[needle.size()-1]){
                int j = 0;
                int start = i;
                while(haystack[i] == needle[j] && j < needle.size()){
                    j++;
                    i++;
                }
                if(j == needle.size()){
                    return start;
                } else{
                    i = start;
                }
            }
            i++;
        }
        return -1;
    }
};
```
