# Grid Unique Paths | Count paths from left-top to the right bottom of a matrix

### Problem Statement:
Given a matrix m X n, count paths from left-top to the right bottom of a matrix with the constraints that from each cell you can either only move to the rightward direction or the downward direction.

#### Example 1:
```
Input Format: m = 2, n= 2
Output: 2
```
##### Explanation: From the top left corner there are total 2 ways to reach the bottom right corner:

Step 1: Right ->> Down
<br>
<img src="https://user-images.githubusercontent.com/63412921/173491013-b3980a5f-b4d4-484b-803c-5e44e4d434a1.png" width="200"/>

Step 2: Down ->> Right
<br>
<img src="https://user-images.githubusercontent.com/63412921/173491030-97a2500d-a8fd-4eef-a681-af82709fe313.png" width="200"/>

#### Example 2:
```
Input Format: m = 2, n= 3 
Ouput: 3
```
##### Explanation:  From the top left corner there is a total of 3 ways to reach the bottom right corner.

Step 1: Right ->> Right ->> Down
<br>
<img src="https://user-images.githubusercontent.com/63412921/173491050-b698e9eb-2040-4550-857b-7b088f652d03.png" width="200"/>

Step 2: Right ->> Down ->> Right
<br>
<img src="https://user-images.githubusercontent.com/63412921/173491066-caad929e-c276-4cff-a403-cefdfad0ca78.png" width="200"/>

Step 3: Down ->> Right->> Right
<br>
<img src="https://user-images.githubusercontent.com/63412921/173491081-a2508703-20fa-4ec4-9089-82e382335442.png" width="200"/>

# Solution:
**Approach:** The approach of this solution is very simple just use a for loop to calculate the m+n-2Cn-1  or m+n-2Cm-1

```java
public int uniquePaths(int m, int n) {
        int N = m+n-2;
        int r = m-1;
        double ans = 1;
        
        for(int i=1;i<=r;i++){
            ans = ans*(N-r+i)/i;
        }
        return (int)ans;
    }
```
