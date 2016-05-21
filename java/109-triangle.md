[109. Triangle](http://www.lintcode.com/problem/triangle)

- [prev: 108. Palindrome Partitioning II](108-palindrome-partitioning-ii.md)
- [next: 110. Minimum Path Sum](110-minimum-path-sum.md)

---

put your own notes and solutions here.
you can add any reference link such as [title](reference url) here.


**Traverse but time limit excedeed**
```
public class Solution {
    /**
     * @param triangle: a list of lists of integers.
     * @return: An integer, minimum path sum.
     */
    private int min;
    public int minimumTotal(int[][] triangle) {
        // write your code here
        min = Integer.MAX_VALUE;
        traverse(triangle, 0 ,0, 0);
        return min;
    }
    //minimum path value from x,y to bottom, sum exclude itself.
    private void traverse(int[][] triangle, int x, int y, int sum){
        //return 
        if(x == triangle.length){
            min = Math.min(min, sum);
            return;
        }
        
        
        traverse(triangle, x + 1, y, sum + triangle[x][y]);
        traverse(triangle, x + 1, y + 1, sum + triangle[x][y]);
    }
}

```
**DFS + memorization**
```
public class Solution {
    /**
     * @param triangle: a list of lists of integers.
     * @return: An integer, minimum path sum.
     */
    public int minimumTotal(int[][] triangle) {
        // write your code here
        int n = triangle.length;
        int [][] hash = new int[n][n];
        //Initializate
        for(int i = 0; i < n; i++){
            for(int j = 0; j < n; j++){
                hash[i][j] = Integer.MAX_VALUE;
            }
        }
        return divideConquer(triangle, hash, 0, 0);
    }
    //minimum path value from x,y to bottom
    private int divideConquer(int[][] triangle,int[][]hash, int x,int y){
        //boundary case
        int n = triangle.length;
        if(x  == n - 1){
            return triangle[x][y];
        }
        //or
        // if(x == n){
        //     return 0;
        // }
        if(hash[x][y] != Integer.MAX_VALUE){
            return hash[x][y];
        }
        
        hash[x][y] = triangle[x][y] + Math.min(divideConquer(triangle, hash, x + 1, y),divideConquer(triangle, hash, x + 1,y + 1));
        return hash[x][y];
    }
}
```
**Bottom-up**
```
public class Solution {
    /**
     * @param triangle: a list of lists of integers.
     * @return: An integer, minimum path sum.
     */
    public int minimumTotal(int[][] triangle) {
        // write your code here
        if(triangle == null || triangle.length == 0){
            return -1;
        }
        if(triangle[0] == null ||triangle[0].length == 0 ){
            return -1;
        }
        
        int n = triangle.length;
        int [][] f = new int [n][n];//minimum path from x,y to bottom
        // Initialize
        for (int i = 0; i < n; i++){
            f[n - 1][i] = triangle[n - 1][i];
        }
        
        for(int i = n - 2; i >= 0; i--){
            for(int j = 0; j <= i; j++){
                f[i][j] = Math.min(f[i + 1][j], f[i + 1][j + 1]) + triangle[i][j];
            }
        }
        return f[0][0];
    }
}

```
**Top down**
*caution:the initialization of i and j !  not 0*
```
public class Solution {
    /**
     * @param triangle: a list of lists of integers.
     * @return: An integer, minimum path sum.
     */
    public int minimumTotal(int[][] triangle) {
        // write your code here
        if(triangle == null || triangle.length == 0){
            return -1;
        }
        if(triangle[0] == null || triangle[0].length == 0){
            return -1;
        }
        //State :minimum path from 0,0 to x,y
        int n = triangle.length;
        int [][] f = new int[n][n];
        //Initialize since not every node have left-top and right-top
        f[0][0] = triangle[0][0];
        for(int i = 1; i< n; i++){
            f[i][0] = f[i - 1][0] + triangle[i][0];
            f[i][i] = f[i - 1][i - 1] + triangle[i][i];
        }
        //top-down !caution:the initialization of i and j !  not 0
        for(int i = 1; i < n; i++){
            for(int j = 1; j < i; j++){
                f[i][j] = Math.min(f[i - 1][j - 1], f[i - 1][j]) + triangle[i][j]; 
            }
        }
        int best = f[n - 1][0];
        for(int i = 0;i < n; i++){
            best = Math.min(best, f[n - 1][i]);
        }
        return best;
    }
}

```
---

- [prev: 108. Palindrome Partitioning II](108-palindrome-partitioning-ii.md)
- [next: 110. Minimum Path Sum](110-minimum-path-sum.md)
