#54. Spiral Matrix
![image](https://user-images.githubusercontent.com/76566137/208917031-c1006618-7fb1-4d75-a288-38854ca0c09b.png)

#Problem Statement
Given an m x n matrix, return all elements of the matrix in spiral order.

# Intuition
I did the most straightforward method, which was to mimic the traversal of the spiral pathway through them matrix, slowly closing in the "walls" of the matrix as each border was reached.

# Approach
I kept track of the min/max rows/cols and adjusted them accordingly. To keep track of "direction" (left, right, down, up), I used the modulus operator. An overall while loop kept the process going until all $$m . n$$ values in the matrix were read.
# Complexity
- Time complexity:
$$O(m.n)$$ because each value in the matrix must be read.

- Space complexity:
$$O(1)$$ because while the output matrix contains all $$m.n$$ values, this is not included in the space complexity.

# Code
```
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        int maxRow = matrix.size();
        int maxCol = matrix[0].size();
        int minRow = 0;
        int minCol = 0;
        int numVals = maxRow * maxCol;
        int dir = 0; // 0 right, 1 down, 2 left, 3 up
        vector<int> output;
        int i = 0;
        int j = 0;
        while(output.size() < numVals) {
            while((i >= minRow && i< maxRow) && (j >= minCol && j < maxCol)){
                output.push_back(matrix[i][j]);
                if(dir == 0){ // right
                    j++;
                }else if (dir == 1) { // down
                    i++;
                }else if (dir == 2){ // left
                    j--;
                }else if (dir == 3) { // up
                    i--;
                }
    
            }
            switch(dir){
                case 0: // right
                    j--;
                    i++;
                    minRow++;
                    break;
                case 1: // down
                    i--;
                    j--;
                    maxCol--;
                    break;
                case 2: // left
                    j++;
                    i--;
                    maxRow--;
                    break;
                case 3: // up
                    i++;
                    j++;
                    minCol++;
                    break;
            }
            dir = (dir + 1) % 4;
        }
        return output;
    }
};
```
