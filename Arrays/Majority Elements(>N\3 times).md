# Majority Elements(>N/3 times) | Find the elements that appears more than N/3 times in the array

#### Problem Statement:
Given an array of N integers. Find the elements that appears more than N/3 times in the array. If no such element exists, return an empty vector.

#### Example 1:
```
Input: N = 5, array[] = {1,2,2,3,2}

Ouput: 2

Explanation: Here we can see that the Count(1) = 1, Count(2) = 3 and Count(3) = 1.Therefore, the count of 2 is greater than N/3 times. Hence, 2 is the answer.
```
#### Example 2:
```
Input:  N = 6, array[] = {11,33,33,11,33,11}

Output: 11 33

Explanation: Here we can see that the Count(11) = 3 and Count(33) = 3. Therefore, the count of both 11 and 33 is greater than N/3 times. Hence, 11 and 33 is the answer.
```
# Solution:
This solution is optimised but as it has used extra space it can be better.
```java
public List<Integer> majorityElement(int[] nums) {
        HashMap<Integer,Integer> mp = new HashMap<>();
        ArrayList<Integer> list = new ArrayList<>();
        for(int i:nums){
            if(mp.containsKey(i)){
                mp.put(i,mp.get(i)+1);
            }
            else{
                mp.put(i,1);
            }
        }
        int max = (int)nums.length/3;
        for(Map.Entry<Integer,Integer> ent1:mp.entrySet()){
            if(ent1.getValue()>max){
                list.add(ent1.getKey());
            }
        }
        
        return list;
}
```
This solution is best optimised and it uses **Boyer Moore Voting Algorithm**
```java
public List<Integer> majorityElement(int[] nums) {
        int num1 = -1;
        int num2 = -1;
        int c1=0;
        int c2=0;
        for(int ele:nums){
            if(ele==num1) c1++;
            else if(ele==num2) c2++;
            else if(c1==0){
                num1 = ele;
                c1 = 1;
            }
            else if(c2 == 0){
                num2 = ele;
                c2 = 1;
            }
            else{
                c1--;
                c2--;
            }
        }
        ArrayList < Integer > ans = new ArrayList < Integer > ();
    c1 = 0;
    c2 = 0;
    int len = nums.length;
    for (int i = 0; i < nums.length; i++) {
      if (nums[i] == num1)
        c1++;
      else if (nums[i] == num2)
        c2++;
    }
    if (c1 > len / 3)
      ans.add(num1);
    if (c2 > len / 3)
      ans.add(num2);
    return ans;
  
    }
```
