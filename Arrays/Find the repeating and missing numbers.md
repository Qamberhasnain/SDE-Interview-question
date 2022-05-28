# Find the repeating and missing numbers

### Problem Statement:
You are given a read-only array of N integers with values also in the range [1,N] both inclusive. Each integer appears exactly once except A which appears twice and B which is missing. The task is to find the repeating and missing numbers A and B where A repeats twice and B is missing.

**Example 1:**
```
Input Format:  array[] = {3,1,2,5,3}

Result: {3,4)

Explanation: A = 3 , B = 4 
Since 3 is appearing twice and 4 is missing
```
**Example 2:**
```
Input Format: array[] = {3,1,2,5,4,6,7,5}

Result: {5,8)

Explanation: A = 5 , B = 8 
Since 5 is appearing twice and 8 is missing
```

# Solution:
### 1:- Using frequency array.
Time complexity is **O(N)** and Space complexity is **O(N)**
```java
public int[] repeatedNumber(final int[] A) {
        int n = A.length;
        int miss, repeat;
        int[] ans = new int[2];
        int freq[] = new int[n+1];
        for(int i=0;i<n;i++){
            freq[A[i]]++;
        }
        for(int j=1;j<=n;j++){
            if(freq[j]==0){
                miss = j;
                ans[1] = miss;
            }
            if(freq[j]>1){
                repeat = j;
                ans[0] = repeat;
            }
        }        
        return ans;
    }
```
### 2:- Using Maths.
Time complexity is **O(N)** and Space complexity is **O(1)**
```java
 public int[] repeatedNumber(final int[] A) {
        long n = A.length;
        long S = (n*(n+1))/2;
        long P = (n*(n+1)*(2*n+1))/6;
        long miss = 0, repeat = 0;
        int[] ans = new int[2];
        for(int i=0;i<n;i++){
            S -= (long) A[i];
            P -= (long)A[i]*(long)A[i];
        }
        miss = (S+P/S)/2;
        repeat = miss - S;
        ans[0] = (int)repeat;
        ans[1] = (int)miss;
        return ans;
    }
```
