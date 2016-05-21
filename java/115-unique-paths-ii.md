[115. Unique Paths II](http://www.lintcode.com/problem/unique-paths-ii)

- [prev: 114. Unique Paths](114-unique-paths.md)
- [next: 116. Jump Game](116-jump-game.md)

---

put your own notes and solutions here.
you can add any reference link such as [title](reference url) here.

**why do I need to break instead of let ```f[i][0] = 0``` ?**

```
public class Solution {
    /**
     * @param obstacleGrid: A list of lists of integers
     * @return: An integer
     */
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        if(obstacleGrid == null || obstacleGrid.length == 0 || obstacleGrid[0].length == 0){
            return 0;
        }
        
        // write your code here
        int m = obstacleGrid.length;
        int n = obstacleGrid[0].length;
        int [][] f = new int[m][n];
        //Initialize
        for(int i = 0; i < m; i++){
            if(obstacleGrid[i][0] != 1){
                f[i][0] = 1;
            }
            else{
                break;// why break?
            }
        }
        
        for(int j = 0; j < n; j++){
            if(obstacleGrid[0][j] != 1){
                f[0][j] = 1;
            }
            else{
                break;
            }
        }
       
       for(int i = 1; i < m; i++){
           for(int j = 1; j < n; j++){
               if(obstacleGrid[i][j] != 1){
                   f[i][j] = f[i - 1][j] + f[i][j - 1];
               }
               else{
                   f[i][j] = 0;
               }
           }
       } 
       return f[m - 1][n - 1];
        
    }
}
```
---

- [prev: 114. Unique Paths](114-unique-paths.md)
- [next: 116. Jump Game](116-jump-game.md)
