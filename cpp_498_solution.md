# [498. Spiral Matrix](https://leetcode.com/problems/spiral-matrix/solutions/2935537/c-spiral-matrix-solution/) (Linked to Leetcode solution)

![image](https://user-images.githubusercontent.com/76566137/208916743-b6c4b18a-4cd3-490a-b59f-676d9019db89.png)

# Problem statement
Given an m x n matrix mat, return an array of all the elements of the array in a diagonal order.
# Intuition
My intuition was to simulate the traversal of the "pointer" outright, but this turned out to be overly complex as I had to account for 8 (technically 6) conditions when the pointer was out of bounds for each edge, and two corners. I spent roughly 3 hours until I finally gave up and looked at the solution. Following the approach of just reading diagonals from top right to bottom left and then reversing the order of the read copy, I was able to solve the problem.
# Approach
I read each diagnoal from top right to bottom left of the matrix and copy the contents into a temporary vector. I then copy the contents into the output vector from index 0 to size - 1 or vice versa depending on which diagonal is being read. If it's an odd diagonal, the contents need to be copied in *opposite* order, since they need to be copied as if they were read in diagonal from bottom left to top right. 

# Complexity
- Time complexity:
Given an $$n.m$$ matrix, the time complexity is $$O(n . m)$$ because we have to read every element of the matrix, of which there are n*m. 

- Space complexity:
Space complexity is $$O(min(n,m))$$ because the largest copy that can be made begins at the top right diagonal and will extend until it goes out of bounds on the bottom of the matrix (meaning the copy is restricted by $$n$$ or the number of rows) or the left side of the matrix, meaning the copy is restricted by $$m$$, or the number of columns.

# Code
```
class Solution {
public:
    vector<int> findDiagonalOrder(vector<vector<int>>& mat) {
        int numCols = mat[0].size();
        int numRows = mat.size();
        vector<int> output;
        int rowIdx = 0;
        int colIdx = 0;
        int diagonal =0; //evens are up & right, odds are down & left
        for(int j = 0; j < numCols; j++) {
            int i = 0;
            int k = j;
            vector<int> temp;
            while((i < numRows) && (k >= 0)) {
                temp.push_back(mat[i][k]);
                i++;
                k--;
            }
            if(diagonal %2 != 0){
                for(int x = 0; x < temp.size(); x++){
                    output.push_back(temp[x]);
                }
            } else {
                for(int x = temp.size() -1; x >=0; x--){
                    output.push_back(temp[x]);
                }
            }
            diagonal++;
        }
        for(int i = 1; i < numRows; i++){
            int j = numCols -1;
            int k = i;
            vector<int> temp;
            while((k < numRows) && j >= 0) {
                temp.push_back(mat[k][j]);
                k++;
                j--;
            }
            if(diagonal %2 != 0){
                for(int x = 0; x < temp.size(); x++){
                    output.push_back(temp[x]);
                }
            } else {
                for(int x = temp.size() -1; x >=0; x--){
                    output.push_back(temp[x]);
                }
            }
            diagonal++;
        }
        return output;
    }
};
```
