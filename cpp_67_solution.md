# [67. Add Binary](https://leetcode.com/problems/add-binary/description/)
# [My solution](https://leetcode.com/problems/add-binary/solutions/2951525/add-binary-c-solution/)

![image](https://user-images.githubusercontent.com/76566137/209486613-e3af0279-6219-4fa3-9111-c9ed4b5f6be3.png)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My intution was to solve this problem similary to the interger array solution. While there are certainly better performing or more elegant ways to solve the problem, this ended up working out in the end.
# Approach
I determined which of the strings was larger and then appended "0" to the smaller string until both were of equal length. I then did binary addition, carrying over values as appropriate and assigning the results to the output string. At the end, if there was a carry of 1, I prepended "1" to the output string before returning it. 

# Complexity
- Time complexity:
The time complexity is $$O(n - m)$$ where $$n$$ and $$m$$ are the lengths of strings the largest and smallest strings respectively. We perform $$n - m$$ operations to make the smallest string equal to the length of the biggest string. We then perform an additional $$n$$ operations to perform binary addition on each of the $$n$$ characters.

- Space complexity:
Space complexity is $$O(n + m)$$ because I created copies of the input strings to rename them as big/small (although this wasn't strictly necessary).

# Code
```
class Solution {
public:
    string addBinary(string a, string b) {
        string big = a;
        string small = b;
        if (b.size() > a.size()) {
            big = b;
            small = a;
        }
        while(big.size() != small.size()){
            small = "0" + small;
        }
        string output(big.size(),'x');
        int x = 0;
        int y = 0;
        int result = 0;
        int carry = 0;
        for(int i = big.size() -1; i>=0; i--){
            if(big[i] == '1'){
                x = 1;
            } else {
                x = 0;
            }
            if(small[i] == '1'){
                y = 1;
            }else {
                y = 0;
            }
            result = x + y + carry;
            if(result >= 2){
                result -=2;
                carry = 1;
            }else{
                carry = 0;
            }
            output[i] = '0' + result;
        }
        if(carry == 1){
            output = "1" + output;
        }
        return output;
    }
};
```
