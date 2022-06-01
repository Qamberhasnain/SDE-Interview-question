# Count inversions in an array

### Problem Statement:
Given an array of N integers, count the inversion of the array (using merge-sort).
What is an inversion of an array? Definition: for all i & j < size of array, if i < j then you have to find pair (A[i],A[j]) such that A[j] < A[i].

#### Example 1:
```
Input Format: N = 5, array[] = {1,2,3,4,5}

Result: 0

Explanation: we have a sorted array and the sorted array 
has 0 inversions as for i < j you will never find a pair 
such that A[j] < A[i]. More clear example: 2 has index 1 
and 5 has index 4 now 1 < 5 but 2 < 5 so this is not an 
inversion.
```
#### Example 2:
```
Input Format: N = 5, array[] = {5,4,3,2,1}

Result: 10

Explanation: we have a reverse sorted array and we will 
get the maximum inversions as for i < j we will always 
find a pair such that A[j] < A[i]. 
Example: 5 has index 0 and 3 has index 2 now (5,3) pair 
is inversion as 0 < 2 and 5 > 3 which will satisfy out 
conditions and for reverse sorted array we will get 
maximum inversions and that is (n)*(n-1) / 2.

For above given array there is 4 + 3 + 2 + 1 = 10 inversions.
```
# Solution:
**First Solution**
This solution is using mergsort algorithm with inversion count variable as global or static variable. Some code testing software has problem in testing multiple test cases if the code has any global variable. So move to the second solution.
```java
static long invCount = 0;
    public static long getInversions(long arr[], int n) {
        mergeSort(arr,0,n-1);
        return invCount;
    }
    public static long[] mergeSort(long[] arr, int lo, int hi){
        if(lo==hi){
            long[] sarr = new long[1];
            sarr[0] = arr[lo];
            return sarr;
        }
        int mid = (lo+hi)/2;
        long[] left = mergeSort(arr,lo,mid);
        long[] right = mergeSort(arr,mid+1,hi);
        long[] merged = mergeTwoArrays(left,right);
        return merged;
    }
    public static long[] mergeTwoArrays(long[] left,long[] right){
        int i=0, j=0,k=0;
        long[] merged = new long[left.length+right.length];
        while(i<left.length&&j<right.length){
            if(left[i]<=right[j]){
                merged[k] = left[i];
                i++;
                k++;
            }
            else{
                invCount += (left.length-i);
                merged[k] = right[j];
                j++;
                k++;
            }
        }
        while(i<left.length){
            merged[k] = left[i];
            i++;
            k++;
        }
        while(j<right.length){
            merged[k] = right[j];
            j++;
            k++;
        }
        return merged;
    }
```
**Second Solution**
This solution is a bit complicated as it doesn't use a global variable and made many changes in mergesort algorithm.
```java
    static long inversionCount(long arr[], long N){
        return mergeSortAndCount(arr, 0, (int)arr.length - 1);
    }
    private static long mergeAndCount(long[] arr, int l, int m, int r){
 
        // Left subarray
        long[] left = Arrays.copyOfRange(arr, l, m + 1);
 
        // Right subarray
        long[] right = Arrays.copyOfRange(arr, m + 1, r + 1);
 
        int i = 0, j = 0, k = l;
        long swaps = 0;
 
        while (i < left.length && j < right.length) {
            if (left[i] <= right[j])
                arr[k++] = left[i++];
            else {
                arr[k++] = right[j++];
                swaps += (long)(m + 1) - (l + i);
            }
        }
        while (i < left.length)
            arr[k++] = left[i++];
        while (j < right.length)
            arr[k++] = right[j++];
        return swaps;
    }
 
    // Merge sort function
    private static long mergeSortAndCount(long[] arr, int l, int r){
 
        // Keeps track of the inversion count at a
        // particular node of the recursion tree
        long count = 0;
 
        if (l < r) {
            int m = (l + r) / 2;
 
            // Total inversion count = left subarray count
            // + right subarray count + merge count 
 
            // Left subarray count
            count += mergeSortAndCount(arr, l, m);
 
            // Right subarray count
            count += mergeSortAndCount(arr, m + 1, r);
 
            // Merge count
            count += mergeAndCount(arr, l, m, r);
        }
        return count;
    }
```
