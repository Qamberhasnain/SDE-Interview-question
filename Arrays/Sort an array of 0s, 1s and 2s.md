# Sort an array of 0s, 1s and 2s
### Problem Statement:
Given an array consisting of only 0s, 1s and 2s. Write a program to in-place sort the array without using inbuilt sort functions. ( Expected: Single pass-O(N) and constant space)

#### Example 1:
```
Input: nums = [2,0,2,1,1,0]
Output: [0,0,1,1,2,2]

Input: nums = [2,0,1]
Output: [0,1,2]
```

# Solution
The algorithm used is **_Dutch national flag algorithm_** with Single pass-**O(N)**
```java
public void sortColors(int[] nums) {
        int lo = 0;
        int mid = 0;
        int hi = nums.length -1;
        int temp;
        while(mid<=hi){
            switch(nums[mid]){
                case 0: {
                    temp = nums[lo];
                    nums[lo] = nums[mid];
                    nums[mid] = temp;
                    lo++;
                    mid++;
                    break;
                }
                case 1: {
                    mid++;
                    break;
                }
                case 2: {
                    temp = nums[hi];
                    nums[hi] = nums[mid];
                    nums[mid] = temp;
                    hi--;
                    break;
                }
            }
        }
    }
```
