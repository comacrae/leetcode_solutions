# [158. Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/description/)

# [Solution](https://leetcode.com/problems/reverse-words-in-a-string/solutions/2969164/c-solution-using-reverse-erase-explained-step-by-step/)

![image](https://user-images.githubusercontent.com/76566137/210028803-dfe0ca59-9b85-4010-a5fc-4ad1584865d7.png)


# Intuition
I wasn't able to figure out this problem without looking at the solution and even then I struggled to understand the second solution described until I literally took an example problem and went through it step-by-step. In order to reinforce my understanding, I would like to share a pictoral step-by-step runthrough of the entire algorithm.

# Approach
I posted a [Youtube](https://youtu.be/1Rix-C-RxHs) video going through the algorithm step-by-step

# Complexity
- Time complexity:
$$O(n)$$ because we're iterating through the array.

- Space complexity:
$$O(1)$$ because we perform in place.

# Code
```
class Solution {
  public:
  string reverseWords(string s) {
    // reverse the whole string
    reverse(s.begin(), s.end());

    int n = s.size();
    int idx = 0;
    for (int start = 0; start < n; ++start) {
      if (s[start] != ' ') {
        // go to the beginning of the word
        if (idx != 0) s[idx++] = ' ';

        // go to the end of the word
        int end = start;
        while (end < n && s[end] != ' ') s[idx++] = s[end++];

        // reverse the word
        reverse(s.begin() + idx - (end - start), s.begin() + idx);

        // move to the next word
        start = end;
      }
    }
    s.erase(s.begin() + idx, s.end());
    return s;
  }
};
```
