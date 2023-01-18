#[36. Valid Sudoku](https://leetcode.com/problems/valid-sudoku/description/)

#[My Solution](https://leetcode.com/problems/valid-sudoku/solutions/3070402/c-solution/)

![image](https://user-images.githubusercontent.com/76566137/213317076-e9afceb2-33a8-4f4a-bc80-8555003f426e.png)


# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My intution was to use a hashset to store the digit chars currently encountered and then iterate through each row, each column, and each 3x3 square.

# Approach
<!-- Describe your approach to solving the problem. -->
I initalized an empty char hashset and iterated through each row, column, and square. If the char at the current index wasn't a  '.' (i.e. was a filled position), I checked to see if it was a digit char that had been encountered in the current row/col/square. If it hadn't been encountered, I added it to the set; otherwise I returned false to indicate that the sudoku grid was invalid. 

The only tricky part was determining if the 3x3 squares were valid. To check this, I had to not just iterate over rows/cols, but carefully update the `i` and `j` values I was using to maintain the 3x3 square format. 
# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$$O(1)$$ only because the sudoku grid is 9x9, thus a constant (though admittedly large and certainly suboptimal) number of steps occur to check the entire grid.

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$$O(1)$$ as the same hashset is used to store the (up to) 9 values encountered.

# Code
```
class Solution {
public:
    bool inSet(unordered_set<char> & set, char c){
        if(set.count(c)){
           return true; 
        }else{
            set.insert(c);
        }
        return false;
    }
    bool isValidSudoku(vector<vector<char>>& board) {
        unordered_set<char> set;
        for(int i = 0; i < 9; i++){ // check each row
            set.clear();
            for(int j = 0; j <9;j++){
                char c = board[i][j];
                if(c != '.'){
                    if(inSet(set, c)){
                        return false;
                    }
                }
            }
        }
        for(int j = 0; j < 9; j++){ // check each column
            set.clear();
            for(int i = 0; i <9;i++){
                char c = board[i][j];
                if(c != '.'){
                    if(inSet(set, c)){
                        return false;
                    }
                }
            }
        }
    for(int k = 0; k < 9; k+=3){
        for(int l = 0; l < 9; l += 3){
            set.clear();
            for(int i = k; i < k + 3; i ++){
                for(int j = l; j < l +3; j++){
                    char c = board[i][j];
                    if(c != '.'){
                        if(inSet(set, c)){
                            return false;
                        }
                    }
                }
            }
        }
    }
        return true;
    }
};
```
