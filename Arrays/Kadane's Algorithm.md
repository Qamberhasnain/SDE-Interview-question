# Kadane’s Algorithm : Maximum Subarray Sum in an Array
### Problem statement:
Given an integer array arr, find the contiguous subarray (containing at least one number) which
has the largest sum and return its sum and print the subarray.

### Examples:

#### Example 1:
```
Input: arr = [-2,1,-3,4,-1,2,1,-5,4] 

Output: 6 

Explanation: [4,-1,2,1] has the largest sum = 6. 
```

#### Examples 2: 
```
Input: arr = [1] 

Output: 1 

Explanation: Array has only one element and which is giving positive sum of 1. 
```
# Solution

```java
public int maxSubArray(int[] nums) {
        
        int sum = 0;
        int max = nums[0];
        if(nums.length == 1){
            return nums[0];
            }
        for(int i=0;i<nums.length;i++){
            sum += nums[i];
            
            if(sum>max){
                max = sum;
            }
            if(sum<0){
                sum = 0;
            }
        }
        return max;
}
```
