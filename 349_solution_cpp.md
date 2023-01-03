# [349. Intersection of Two Arrays](https://leetcode.com/problems/intersection-of-two-arrays/description/)

# [My Solution](https://leetcode.com/problems/intersection-of-two-arrays/solutions/2994400/c-solution-credit-goes-to-user-benkemal/)

![image](https://user-images.githubusercontent.com/76566137/210439431-9c5b29b7-6dc6-459a-aeb8-f569f68ba632.png)

# Intuition
My original approach was very naive - I just made two hashsets and then added the overlapping values of said sets to the output array. User [benkemal](https://leetcode.com/benkemal/) made a very good point in the comments of the official LeetCode solution - we don't need a second hashset. His solution was in Java, so I adapted it to C++ here.

# Approach
<!-- Describe your approach to solving the problem. -->
First, we go through all the values of one array (it doesn't matter which, so lets call this array $$X$$), inserting each element into a hashset $$H$$. 

At this point, $$H$$ contains all the unique values in $$X$$. 

We then iterate through all the values of the second array (array $$Y$$). If a given value $$y$$ in $$Y$$ exists in $$H$$, we do the following:

1) Add the value to the output array.
2) Remove the value from $$H$$. 

We do the second step because it prevents an overlapping value in $$X$$ and $$Y$$ being added more than once to the output array. 

Once we've iterated through $$Y$$, we're done!
# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$$O(n + m)$$ where $$n$$ is the length of the first array and $$m$$ is the length of the other.
- Space complexity:
$$O(n)$$ for constructing the hashset for the first array. 

# Code
```
class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {
        unordered_set<int> set1;
        vector<int> output;
        for(int i : nums1){
            set1.insert(i);
        }
        for(int i : nums2){
            if(set1.count(i) > 0){
                output.push_back(i);
                set1.erase(i);
            }
        }
        return output;
    }
};
```
