# [Moving Average From Data Stream](https://leetcode.com/problems/moving-average-from-data-stream/description/)

# [My Solution](https://leetcode.com/problems/moving-average-from-data-stream/solutions/3103374/c-solution/)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My intuition was a sort of brute-force approach using a queue, but I realized after looking at the solution that things could be done much more elegantly by keeping a running sum instead of adding all values in the sliding window each time.
# Approach
<!-- Describe your approach to solving the problem. -->
I keep track of the following values:
* a running sum (`sum`)
* the given size of the window (`size`)

Using these values, when the `next` function is called, I check if the current queue size is equal to the window size. If so, I subtract the value at the front of the queue (i.e. the leftmost value of the sliding window) from the running sum and pop it from the queue. 

Then no matter what, I add the new value to the running sum and I push the new value into the queue.

Finally, I return the value of the running sum divided by the size of the current queue.

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$$O(1)$$ because nothing is iterated over.
- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$$O(n)$$ where $$n$$ is the size of the sliding window.
# Code
```
class MovingAverage {
public:
    queue<int> q;
    int size =0;
    double sum = 0;
    MovingAverage(int size) {
        this -> size = size;
    }
    
    double next(int val) {
        if(size == q.size()){
            sum -= q.front();
            q.pop();
        }
        sum += val;
        q.push(val);
        return sum / q.size();
    }
};

/**
 * Your MovingAverage object will be instantiated and called as such:
 * MovingAverage* obj = new MovingAverage(size);
 * double param_1 = obj->next(val);
 */
```
