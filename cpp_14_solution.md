# [14. Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/description/)

# [Solution](https://leetcode.com/problems/longest-common-prefix/solutions/2954733/14-longest-common-prefix-solution/)

![image](https://user-images.githubusercontent.com/76566137/209573945-359a0e9b-36bb-430b-9196-203432fdb193.png)


# Intuition
My intuition was to iterate over each of the strings in the `strs` vector, keeping a track of the following:
* if the current char matches for index $$x$$
* if index $$x$$ is out of bounds for a given string

# Approach
I implemented the code to execute my intutions described above, looping over the `strs` vector at the current index `charIdx` until either the index counter went out of bounds or a common char was no longer held across all strings.

# Complexity
- Time complexity:
$$O(m * n)$$ where $$m$$ is the length of the shortest string in the `strs` vector and $$n$$ is the number of strings in the `strs` vector.

- Space complexity:
$$O(1)$$ because the tracking variables are constant in size.

# Code
```
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        string output = "";
        int strIdx = 0;
        int charIdx = 0;
        bool common = true;
        bool maxSize = false;
        char c;
        while( maxSize == false && common == true ){
            strIdx = 0;
            if (charIdx < strs[0].size()){
                 c = strs[strIdx][charIdx];           
            }else{
                maxSize == true;
            }
            while (strIdx < strs.size() && maxSize == false){
                if(strs[strIdx].size() == 0){
                    return "";
                }else if( charIdx < strs[strIdx].size()){

                     if (c != strs[strIdx][charIdx]){
                         common = false;
                     }
                 }else{
                     maxSize = true;
                 }
                strIdx++;
            }
            charIdx++;
            if (common == true && maxSize == false){
                output+=c;
            }
        }
        return output;
        
    }
};
```
