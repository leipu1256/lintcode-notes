[110. Minimum Path Sum](http://www.lintcode.com/problem/minimum-path-sum)

- [prev: 109. Triangle](109-triangle.md)
- [next: 111. Climbing Stairs](111-climbing-stairs.md)

---

put your own notes and solutions here.
you can add any reference link such as [title](reference url) here.

**int[m][n] m is row, n is column**
```
public class Solution {
    /**
     * @param grid: a list of lists of integers.
     * @return: An integer, minimizes the sum of all numbers along its path
     */
    public int minPathSum(int[][] grid) {
        // write your code here
        
        if(grid == null || grid.length == 0){
            return -1;
        }
        if(grid[0] == null || grid.length == 0){
            return -1;
        }
        // State :minimum path from (0,0) to (x,y)
        int m = grid.length; // height 
        int n = grid[0].length; // width
        int[][] f= new int[m][n];
        //Initialize
        f[0][0] = grid[0][0];
        for(int i = 1; i < m; i++){
            f[i][0] = f[i - 1][0] + grid[i][0];
        }
        for(int i = 1;i < n; i++){
            f[0][i] = f[0][i - 1] + grid[0][i];  
        }
        
        for(int i = 1; i < m; i++){
            for(int j = 1; j < n; j++){
                f[i][j] = Math.min(f[i - 1][j] , f[i][j - 1]) + grid[i][j]; 
            }
        }
        return f[m-1][n-1];
    }
}
```
---

- [prev: 109. Triangle](109-triangle.md)
- [next: 111. Climbing Stairs](111-climbing-stairs.md)
