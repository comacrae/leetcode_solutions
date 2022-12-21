# [118. Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/description/)

![image](https://user-images.githubusercontent.com/76566137/208936234-da8b359d-be57-412a-88c4-d94880b541af.png)


## [Solution Link](https://leetcode.com/problems/pascals-triangle/solutions/2935871/c-solution/)

# Intuition
My intuition was to try something with recursion, but I wanted to solve it the straight-forward way first (just adding up elements that weren't on the edges, since all edges are 1).
# Approach
In the case of numRows = 1 or 2, I just return the prebuilt triangle. Otherwise, from rows 3 up until N, I added up values from the previous row accordingly.
# Complexity
- Time complexity:
$$O(n^2)$$ because for each row, all values of the previous row are traversed.
- Space complexity:
$O(1) since no extra space is used; everything is done with the matrix reprsenting the triangle and the vector representing the new row to be added. 

# Code
```
class Solution {
public:
    vector<vector<int>> generate(int numRows) {
        if (numRows == 1){
           vector<vector<int>> output{{1}};
            return output;
        } else if (numRows == 2){
            vector<vector<int>> output{{1},{1,1}};
            return output;
        }else {
            vector<vector<int>> output{{1},{1,1}};
            for(int row = 2; row < numRows; row++){
                vector<int> newRow(row+1,1);
                for(int i = 1; i < row; i++){
                        newRow[i] = output[row-1][i-1] + output[row-1][i];
                }
                output.push_back(newRow);
            }
            return output;
        }
    }
};
```
