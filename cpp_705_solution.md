# [705. Hash Set Implementation Using Linked List](https://leetcode.com/problems/design-hashset/description/)
# [My Solution](https://leetcode.com/problems/design-hashset/solutions/2982073/c-solution-using-linked-list-and-modulo-operator/)

![image](https://user-images.githubusercontent.com/76566137/210188416-ebea415f-b647-4ba9-9462-6428cdb495aa.png)


# Intuition
After much struggling to implement a linked list of my own, I used the std library linked list (`list`) and made a vector of lists. I made a simple hash function using the modulo (`%`) operator.

# Approach
Because I used the std implementation it was fairly straightforward. I made a vector of type `list<int>`, where each list represents a "bucket". I chose to make the set consist of 997 buckets because this was the greatest prime number below 1000; apparently [prime numbers are better to use for modulo-based hash functions](https://computinglife.wordpress.com/2008/11/20/why-do-hash-functions-use-prime-numbers/).

# Complexity
- Time complexity: given $$N$$ possible values over $$K$$ buckets and assuming that the $$N$$ values are *distributed evenly* over the $$K$$ buckets, the `add`, `remove`, and `contains` functions have time complexity $$O(N/K)$$ because in the worst case, a given bucket has $N/K$ values, and the desired value is at the end of the list in the case of the `remove` function, or in the case of the `contains` and `add` functions, the entire list must be traversed.


- Space complexity:
$$O(M + K)$$ where $$M$$ is the number of *unique* values and $$K$$ is the number of buckets. We only consider unique values because those are the only ones that are stored.

# Code
```
class MyHashSet {
public:
    vector<list<int>> mySet;
    MyHashSet() { 
        mySet = vector<list<int>>(997);
    }

    void add(int n){
        mySet[_hash(n)].push_back(n);
    }
    void remove(int n){
        mySet[_hash(n)].remove(n);
    }
    bool contains(int n){
        bool found = false;
        list<int>& l = mySet[_hash(n)];
        list<int>::iterator it = l.begin();
        list<int>::iterator end = l.end();
        while(it != end && ! found){
            if(*it == n)
                found = true;
            it++;
        }
        return found;
    }
    int _hash(int n){
        return n % 997;
    }
};
/**
 * Your MyHashSet object will be instantiated and called as such:
 * MyHashSet* obj = new MyHashSet();
 * obj->add(key);
 * obj->remove(key);
 * bool param_3 = obj->contains(key);
 */
```
