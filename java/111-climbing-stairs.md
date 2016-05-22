[111. Climbing Stairs](http://www.lintcode.com/problem/climbing-stairs)

- [prev: 110. Minimum Path Sum](110-minimum-path-sum.md)
- [next: 112. Remove Duplicates from Sorted List](112-remove-duplicates-from-sorted-list.md)

---

put your own notes and solutions here.
you can add any reference link such as [title](reference url) here.

***recursive : time limit exceded***

```
public class Solution {
    /**
     * @param n: An integer
     * @return: An integer
     */
    public int climbStairs(int n) {
      
        if(n == 1 || n == 0){
            return 1;
        }
        if(n == 2){
            return 2;
        }
        return climbStairs(n - 1) + climbStairs(n - 2);
    }
}
```
 
*** DP***

```
public class Solution {
    /**
     * @param n: An integer
     * @return: An integer
     */
    public int climbStairs(int n) {
        // write your code here
        
        //f[n] from 0 to n
        int[] f= new int[n];
        
        if(n <= 1){
            return 1;
        }
        f[0] = 1;// one stair
        f[1] = 2;// two staris
        
        for (int i = 2; i < n; i++){
            f[i] = f[i - 1] + f[i - 2];
        }
        return f[n - 1];
       
    }
}

```
---

- [prev: 110. Minimum Path Sum](110-minimum-path-sum.md)
- [next: 112. Remove Duplicates from Sorted List](112-remove-duplicates-from-sorted-list.md)
