#[1. Two Sum](https://leetcode.com/problems/two-sum/description/)

#[My Solution](https://leetcode.com/problems/two-sum/solutions/2999288/c-solution/)

![image](https://user-images.githubusercontent.com/76566137/210616043-0003e212-a179-444d-9c98-f4a88df7cb05.png)

# Intuition
Since this problem was discussed as an example, I just used the suggestion of applying a hashmap to store the index of values.

# Approach
<!-- Describe your approach to solving the problem. -->
I insert all elements from the num vector into the hashmap, using the element as the key and the index of the element as the value. If the element was already encountered, I update the value of the key/value pair to the newer (greater) index. 

Once this is done, I iterate through nums once more, stopping the iteration when either 
a) the end of the nums vector is reached or
b) there exists a key $$k$$ in the hashmap such that given the vector $$V$$ and the current index $$i$$

$$k = target - V[i]$$
which is the same thing as checking if 
$$k + V[i] = target $$. 

If such a key is found, I return the value associated with the key (which is the index of the key in the `nums` vector) along with the index of the current element.
# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$$n$$ steps to iterate through `nums` and $$n/2$$ steps to iterate through nums until finding an element which adds to another element to get the target, and for each of those $$n/2$$ steps, we use the `at` method of the unordered_map. This is worst case $$O(n)$$ time complexity, but on average and for all intents and purposes constant, so we can say generally that the time complexity overall for this algorithm is $$O(n + n/2)$$ = $$O(n)$$.

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$$O(n)$$ to create the hashmap

# Code
```
/*Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.*/

class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> map;
        vector<int> output;
        for(int i = 0; i < nums.size(); i++)
            if(map.count(nums[i]) == 0){
                map.insert(make_pair(nums[i], i)); // store num as key and index as value
            } else{ // add index
                map[nums[i]] = i;
            }
        int i = 0;
        while(i < nums.size() && output.size() != 2){
            if(map.count(target - nums[i]) > 0){
                if(i != map.at(target - nums[i]))
                    output = {i, (map.at(target - (nums[i])))};
            }
            i++;
        }
        return output;
    }
};
```
