#[Mininum Index Sum of Two Lists](https://leetcode.com/problems/minimum-index-sum-of-two-lists/description/)

#[My Solution](https://leetcode.com/problems/minimum-index-sum-of-two-lists/solutions/3041675/c-solution/)

![image](https://user-images.githubusercontent.com/76566137/212133001-ca2438c9-cff8-4eff-8fd2-29450a59dd55.png)

# Intuition
My intuition was to use a hashmap to relate repeated words to their indices found and then adding their values.

# Approach
First, I iterate through *list1* and insert each string to the hashmap using the string as the key and the  **negative** of the index of the string as the value. Then I iterate through the second list. For each string in *list2*, if the string is already in the hashmap, it means it is repeated, so I then get the negative index , multiply it by negative one to make it positive, and add the index of the string in *list2*. 

While this is occuring, I also track the minimum sum value and update it as necessary.

By this point, any strings which are found in both *list1* and *list2* have positive values. I then iterate through the hashmap. For any key value pair where the index (the value) matches the min value I tracked earlier, I add the key( the string) to the output vector. Once the hashmap is iterated through, I return the vector.

# Complexity
- Time complexity:
$$O((m+n) + min(m,n))$$ where $$m$$ and $$n$$ are the lengths of the lists. It is $$min(m,n)$$ because in the worst case, all words in the smaller list are repeated in the larger list.

- Space complexity:
$$O(max(m,n))$$

# Code
```
class Solution {
public:
    vector<string> findRestaurant(vector<string>& list1, vector<string>& list2) {
        unordered_map<string,int> set;
        vector<string> output;
        for(int i = 0; i < list1.size(); i++){
            set[list1[i]] = i * -1;
        }
        int min = list1.size() + list2.size();
        for(int i = 0; i < list2.size() && i <= min;i++){
            if(set.count(list2[i]) > 0){
                int val = (set[list2[i]] * -1) + i;
                set[list2[i]] = val;
                if(val < min)
                    min = val;
            }
        }
        for(unordered_map<string,int>::iterator it = set.begin(); it != set.end(); it++){
            if(it -> second == min){
                output.push_back(it->first);
            }
        }
    return output;
    }

};
```
