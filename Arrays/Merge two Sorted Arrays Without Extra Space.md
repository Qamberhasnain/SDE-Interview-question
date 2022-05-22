# Merge two Sorted Arrays Without Extra Space
### Problem statement:
Given two sorted arrays arr1[] and arr2[] of sizes n and m in non-decreasing order. Merge them in sorted order. Modify arr1 so that it contains the first N elements and modify arr2 so that it contains the last M elements.

#### Examples:
##### GFG Example
```
Input: 
n = 4, arr1[] = [1 4 8 10] 
m = 5, arr2[] = [2 3 9]

Output: 
arr1[] = [1 2 3 4]
arr2[] = [8 9 10]

Explanation:
After merging the two 
non-decreasing arrays, we get, 
1,2,3,4,8,9,10.
```
# GFG Solution:
First solution using GAP algorithm.
```java
public static void merge(long ar1[], long ar2[], int n, int m) 
    {   
        int gap =(int) Math.ceil((double)(n + m) / 2.0);
        long t;
        while (gap > 0) {
            int i = 0;
            int j = gap;
            while (j < (n + m)) {
              if (j < n && ar1[i] > ar1[j]) {
                t = ar1[i];
                ar1[i] = ar1[j];
                ar1[j] = t;
              } else if (j >= n && i < n && ar1[i] > ar2[j - n]) {
                t = ar1[i];
                ar1[i] = ar2[j-n];
                ar2[j-n] = t;
              } else if (j >= n && i >= n && ar2[i - n] > ar2[j - n]) {
                t = ar2[i-n];
                ar2[i-n] = ar2[j-n];
                ar2[j-n] = t;
              }
              j++;
              i++;
            }
            if (gap == 1) {
              gap = 0;
            } else {
              gap =(int) Math.ceil((double) gap / 2.0);
            }
        }
    }
```
Second solution with complexity **O(nlogn)**
```java
public static void merge(long arr1[], long arr2[], int n, int m) 
    {
        int i=n-1, j=0;
        Arrays.sort(arr1);
        Arrays.sort(arr2);
        while(i>=0 && j<m){
            if(arr1[i]>arr2[j]){
                long tmp = arr1[i];
                arr1[i] = arr2[j];
                arr2[j] = tmp;
                i--;
            }
            else{
                j++;
            }
        }
        Arrays.sort(arr1);
        Arrays.sort(arr2);
    }
```
##### Leetcode Example
```
Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
Output: [1,2,2,3,5,6]
Explanation: The arrays we are merging are [1,2,3] and [2,5,6].
The result of the merge is [1,2,2,3,5,6] with the underlined elements coming from nums1.
```
# Leetcode Solution:
```java
public void merge(int[] nums1, int m, int[] nums2, int n) {
        int p1=m-1;
        int p2=n-1;
        int p3 = m+n-1;
        
        
        while(p2>=0){
           
            if(p1>=0 && nums1[p1]>=nums2[p2]){
                nums1[p3]=nums1[p1];
                p3--;
                p1--;
            }else{
                nums1[p3]=nums2[p2];
                p3--;
                p2--;
            }
        } 
}
```
