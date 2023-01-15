#[49. Group Anagrams](https://leetcode.com/problems/group-anagrams/description/)

#[My Solution](https://leetcode.com/problems/group-anagrams/solutions/3052306/c-solution/)

![image](https://user-images.githubusercontent.com/76566137/212504410-f1f2b83a-0c63-4ae7-ae41-f4e2b93829da.png)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My intution was to use a hashmap to keep track of the strings that had been encountered thusfar.
# Approach
<!-- Describe your approach to solving the problem. -->
I made a hashmap where the key was the sorted version of the string observed and the value was the vector of anagrams containing the sorted group of letters. 

For each string in the input vector, I checked to see if the sorted version of the string had been encountered yet by checking the count of the sorted string in the hashmap. If the sorted version HAD been, encountered I added the unsorted version to its respective "anagram set" or string vector.

If the string had NOT been encountered yet, I added a new key value pair to the hashmap where the key was the sorted string and the value was a vector containing the unordered string. 

Once the vector of strings was looped through, I iterated through them again, this time inserting each value (string vector) to an overall output vector.
# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$$O(nklogk)$$ where $$n$$ is the number of strings and $$klogk$$ is the time to sort the largest string using the built-in sorting algorithm.

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$$O(max(n,m))$$ where $$n$$ is the number of strings in the input vector and $$m$$ is the largest set of anagrams for a given collection of letters.

# Code
```
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        unordered_map<string,vector<string>> map;
        vector<vector<string>> output;
        for(int i = 0; i < strs.size(); i++){
            string str = strs[i];
            string tmp = strs[i];
            sort(tmp.begin(),tmp.end());
            if(map.count(tmp) != 0){ // if anagram exists, populate vector
                map[tmp].push_back(str);
            }else{
                map.insert(pair<string,vector<string>>(tmp,vector<string>{str}));
            }
        }
        for(unordered_map<string,vector<string>>::iterator it = map.begin(); it != map.end(); it++){
            
            output.push_back(it -> second);
        }
        return output;
    }
};
```
