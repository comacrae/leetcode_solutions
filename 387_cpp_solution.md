#[387. First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/description/)

#[My Solution](https://leetcode.com/problems/first-unique-character-in-a-string/solutions/3041868/c-solution/)

![image](https://user-images.githubusercontent.com/76566137/212140724-d4da288d-6d38-4f5e-885a-40ffe898312e.png)


# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My intuition was to track which characters in the string had been previously encountered using a hashmap, where the key would be the character and the value would be the index that the character was encountered.
# Approach
<!-- Describe your approach to solving the problem. -->
I create a hashmap where the key is the char and value is the index where the char was encountered.

If it is the first time a char is encountered, the index is placed as the value. If it is the second time, the index is replaced with -1 to indicate the character was encountered more than once.

The hashmap is iterated through and the minimum index is returned. If the minimum is unchanged, then -1 is returned to indicate that there are no unique chars.

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$$O(n)$$ because the string is iterated through once to populate the hashmap and then the hashmap is iterated through once to find the min index.
- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$$O(m)$$ where $$m$$ is the number of unique characters recognizable in the given language.

# Code
```
class Solution {
public:
    int firstUniqChar(string s) {
        unordered_map<char,int> map;
        for(int i = 0; i<s.size(); i++){
            if(map.count(s[i]) == 0)
                map[s[i]] = i;
            else
                map[s[i]] = -1;
        }
        int min = s.size();
        for(unordered_map<char,int>::iterator it = map.begin(); it != map.end(); it++){
            int idx = it -> second;
            if(idx != -1 && idx < min)
                min = idx;
        }
        
        if(min == s.size())
            return -1;
        return min;
    }
};
```
