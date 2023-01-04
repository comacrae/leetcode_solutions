#[205. Isomorphic Strings](https://leetcode.com/problems/isomorphic-strings/description/)

#[My Solution](https://leetcode.com/problems/isomorphic-strings/solutions/2999590/c-na-ve-but-straightforward-solution/)

![image](https://user-images.githubusercontent.com/76566137/210625003-b897abec-47ea-4c12-a87f-4fd016eb8744.png)


# Intuition
My intution was to use a hashmap to map one character to another.

# Approach
<!-- Describe your approach to solving the problem. -->
Given strings $$X$$ and $$Y$$, I mapped character $$x$$ to character $$y$$ as I traversed through $$X$$ first. If $$x$$ already existed in the hashmap and the associated character $$y$$ was different, I knew that the isomorphism wouldn't hold, so I returned false. 

This only checks $$X$$ -> $$Y$$, so we need to check the reverse as well. For instance, with just the first iteration, the case X="abac" Y="abab" would fail because the following pairs would be inserted or checked:
i = 0: insert (a,a)
i = 1: insert (b,b)
i = 2: check  (a,a) is valid
i = 3: insert (c,a) THIS LINE LEADS TO WRONG RETURN VALUE

A simple way to address this is to just clear the map and then reverse the assignment, now checking for $$Y$$ -> $$X$$.
# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$$O(n)$$ because we iterate through the strings twice and they are both of length $$n$$ and the hashmap's `insert` and `count` functions are $$O(1)$$ on average.
- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$$O(n)$$ if each string consists entirely of unique ASCII characters.

# Code
```
class Solution {
public:
    bool isIsomorphic(string s, string t) {
        unordered_map<char,char> map;
        for(int i = 0; i < s.size();i++){
            if(map.count(s[i]) == 0){
                map.insert({s[i],t[i]});
            }else{
                if(map.at(s[i]) != t[i])
                    return false;
            }
        }
        map.clear(); // now we check the other way
        for(int i = 0; i < t.size();i++){
            if(map.count(t[i]) == 0){
                map.insert({t[i],s[i]});
            }else{
                if(map.at(t[i]) != s[i])
                    return false;
            }
        }
        return true;
    }
};
```
