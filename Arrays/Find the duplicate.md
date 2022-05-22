# Find the duplicate in an array of N+1 integers

### Problem Statement:
Given an array of N + 1 size, where each element is between 1 and N. Assuming there is only one duplicate number, your task is to find the duplicate number.

#### Examples:
```
Example 1: 

Input: arr=[1,3,4,2,2]

Output: 2

Explanation: Since 2 is the duplicate number the answer will be 2.
```

# Solution:
Two pointer tortoise method with time complexity as **O(N)** and space complexity as **O(1)** but it is a bit slower than Frequency array method.
```java
public int findDuplicate(int[] nums) {
        int sl = nums[0];
        int fs = nums[0];
        do{
            sl = nums[sl];
            fs = nums[nums[fs]];
        }while(sl!=fs);
        fs = nums[0];
        while(sl!=fs){
            sl = nums[sl];
            fs = nums[fs];
        }
        return sl;
  }
```
Frequencyy array method with time complexity as **O(N)** and space complexity as **O(N)**.
```java
public int findDuplicate(int[] nums) {
        int n = nums.length;
        int freq[] = new int[n + 1];
        for (int i = 0; i < n; i++) {
            if (freq[nums[i]] == 0) {
                freq[nums[i]] += 1;
            } else {
                return nums[i];
            }
        }
        return 0;
  }
```
