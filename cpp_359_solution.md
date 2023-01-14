#[359. Logger Rate Limiter](https://leetcode.com/problems/logger-rate-limiter/description/)

#[My Solution](https://leetcode.com/problems/logger-rate-limiter/solutions/3052191/c-solution/)

![image](https://user-images.githubusercontent.com/76566137/212501800-3b1b25a2-065c-473e-a5dd-f2f737224412.png)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My intution was to use a hashmap to keep track of the last time a message was logged.
# Approach
<!-- Describe your approach to solving the problem. -->
If a message hasn't been logged, then I create a key value pair in my hashmap where the string is the key and the timestamp + 10 (to create a delay) is logged. Otherwise, if the message has been logged, I check if the current timestamp is greater than or equal to the value associated with the message. If so, I set a flag to indicate that the message should be printed again and I update the value to the current timestamp + 10.
# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$$O(1)$$ due to the hashmap insert/search nature.

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$$O(n)$$ where n is the number of elements inserted to the hashmap.

# Code
```
class Logger {
public:
    unordered_map<string,int> msgMap;
    Logger() {

    }
    
    bool shouldPrintMessage(int timestamp, string message) {
        bool print = false;
        if(this -> msgMap.count(message)){ // if message has already been logged
            if(timestamp >= this -> msgMap[message]){
                print = true;
                msgMap[message] = timestamp + 10;
            }
        } else{ // message hasn't been logged
            this -> msgMap[message] = timestamp + 10;
            print = true;
        }
        return print;
    }
};

/**
 * Your Logger object will be instantiated and called as such:
 * Logger* obj = new Logger();
 * bool param_1 = obj->shouldPrintMessage(timestamp,message);
 */
```
