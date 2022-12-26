# [561. Array Partition](https://leetcode.com/problems/array-partition/description/)

# [My Solution](https://leetcode.com/problems/array-partition/solutions/2955190/c-solution-using-quicksort/)

![image](https://user-images.githubusercontent.com/76566137/209582135-8e37bcdf-d4d5-47ff-9744-04d5431e7d1d.png)


# Intuition
After looking at the problem and reading some of the hints, I realized that I had to sort the list. After that it would simply be a matter of summing across even indices.

# Approach
I implemented the quicksort function by hand using the following source as a guideline: https://www.programiz.com/dsa/quick-sort. I then simply returned the sum of the even indices accross the array.

# Complexity
- Time complexity:
$$O(n^2)$$ because this is the time complexity for quicksort (plus the $$n/2$$ steps for addition which are negligible compared to the $$n^2$$ worst case steps for quicksort)

- Space complexity:
$$O(1)$$ because quicksort is in place and no other data structures are used.

# Code
```
class Solution {
public:

    void swap(int * x, int * y){
        int tmp = *x;
        *x = *y;
        *y = tmp;
    }
    int partition(vector<int>&nums,int low, int high){
        int pivot = nums[high]; // begin with rightmost value
        int i = low -1;
        for(int j = low; j < high; j++){
            if(nums[j] <= pivot){
                i++;
                swap(&nums[i],&nums[j]);
            }
        }
        swap(&nums[i +1], &nums[high]);
        return i+1;
    }
    void quickSort(vector<int>&nums, int low, int high){
        if(low < high){
            int pivot = partition(nums, low, high);
            quickSort(nums,low,pivot - 1);
            quickSort(nums,pivot + 1,high);
        }
    }
    int arrayPairSum(vector<int>& nums) {
        int sum = 0;
        quickSort(nums,0,nums.size()-1);
        for(int i = 0; i < nums.size() - 1; i+=2){
            sum += nums[i];
        }
        return sum;
    }
};
```
