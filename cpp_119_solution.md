# [119.Pascal's Triangle](https://leetcode.com/problems/pascals-triangle-ii/description/)

# [Solution](https://leetcode.com/problems/pascals-triangle-ii/solutions/2965743/in-place-c-solution/)

![image](https://user-images.githubusercontent.com/76566137/209907831-042ead35-5fdc-488b-aa50-fd147b53dbda.png)

# Intuition
My intution for solving this problem was to use recursion, but after running through some examples on paper, I realized that I could create an in-place solution by sacrificing time complexity.

# Approach
Say we want to obtain the $$kth$$ row, 0-indexed. Since the $$kth$$ row has $$k + 1 $$ elements, we can initialize an output vector `output` with $$k+1$$ elements where the final element is $$1$$. Then we can iterate over the vector, adding the following element to the current element's value: 
``output[i] = output[i] + output[i+1]``
Of course we will only iterate up to the second-to-last element to avoid going out of bounds. 

If we perform this operation $$k$$ times, the result will be the desired row of Pascal's Triangle.

# Complexity
- Time complexity:
$$O(k^2)$$ because we iterate over $$k$$ elements $$k$$ times.

- Space complexity:
$$O(1)$$ because we don't include space complexity of the output object and all operations are done in-place.

# Code
```
class Solution {
public:
    vector<int> getRow(int rowIndex) {
        vector<int> output(rowIndex +1);
        output[rowIndex] = 1;
        for(int i =0; i < rowIndex;i++) {
            for(int j = 0; j < rowIndex;j++){
                output[j]= output[j] + output[j+1];
            }
        }
        return output;
    }
};
```
