# Count Reverse Pairs

### Problem Statement:
Given an array of numbers, you need to return the count of reverse pairs. Reverse Pairs are those pairs where i<j and arr[i]>2\*arr[j].

#### Example 1:
```
Input: N = 5, array[] = {1,3,2,3,1)

Output: 2 

Explanation: The pairs are (3, 1) and (3, 1) as from both the pairs the condition arr[i] > 2*arr[j] is satisfied.
```
#### Example 2:
```
Input: N = 4, array[] = {3,2,1,4}

Output: 1

Explaination: There is only 1 pair  ( 3 , 1 ) that satisfy the condition arr[i] > 2*arr[j]
```
# Solution:
```java
public int reversePairs(int[] nums) {
        return mergeSort(nums,0,nums.length -1);
    }
    public int mergeSort(int[] nums,int low,int high){
        if(low>=high) return 0;
        int mid=(low+high)/2;
        int inv = mergeSort(nums,low,mid);
        inv += mergeSort(nums,mid+1,high);
        inv += merge(nums,low,mid,high);
        return inv;
    }
    public int merge(int[] nums,int low,int mid,int high){
        int count=0;
        int j=mid+1;
        for(int i=low;i<=mid;i++){
            while(j<=high && nums[i]>(2*(long)nums[j])){
                j++;
            }
            count += (j-(mid+1));
        }
        ArrayList<Integer> temp = new ArrayList<>();
        int left = low, right=mid+1;
        while(left<=mid && right<=high){
            if(nums[left]<=nums[right]){
                temp.add(nums[left++]);
            }
            else{
                temp.add(nums[right++]);
            }
        }
        while(left<=mid){
            temp.add(nums[left++]);
        }
        while(right<=high){
            temp.add(nums[right++]);
        }
        for(int i=low;i<=high;i++){
            nums[i] = temp.get(i-low);
        }
        return count;
    }
```
**For ArrayList**
```java
public int merge(ArrayList<Integer> nums,int low,int mid,int high){
        int count=0;
        int j=mid+1;
        for(int i=low;i<=mid;i++){
            while(j<=high && nums.get(i)>(2*(long)nums.get(j))){
                j++;
            }
            count += (j-(mid+1));
        }
        ArrayList<Integer> temp = new ArrayList<>();
        int left = low, right=mid+1;
        while(left<=mid && right<=high){
            if(nums.get(left)<=nums.get(right)){
                temp.add(nums.get(left++));
                //System.out.println(nums.get(left++));
            }
            else{
                temp.add(nums.get(right++));
                //System.out.println(nums.get(right++));
            }
        }
        while(left<=mid){
            temp.add(nums.get(left++));
        }
        while(right<=high){
            temp.add(nums.get(right++));
        }
        for(int i=low;i<=high;i++){
            nums.set(i,temp.get(i-low));
        }
        return count;
    }
    public int mergeSort(ArrayList<Integer> nums,int low,int high){
        if(low>=high) return 0;
        int mid=(low+high)/2;
        int inv = mergeSort(nums,low,mid);
        inv += mergeSort(nums,mid+1,high);
        inv += merge(nums,low,mid,high);
        return inv;
    }
    public static int reversePairs(ArrayList<Integer> nums) 
    {
        Solution sol = new Solution();
        return sol.mergeSort(nums,0,nums.size()-1);
    }
```
