[136. Palindrome Partitioning](http://www.lintcode.com/problem/palindrome-partitioning)

- [prev: 135. Combination Sum](135-combination-sum.md)
- [next: 137. Clone Graph](137-clone-graph.md)

---

put your own notes and solutions here.
you can add any reference link such as [title](reference url) here.

**long time no code = = life is so hard**
***recursive way***
```
public class Solution {
    /**
     * @param s: A string
     * @return: A list of lists of string
     */
    public ArrayList<ArrayList<String>> partition(String s) {
        // write your code here
        ArrayList<ArrayList<String>> result = new ArrayList<ArrayList<String>>();
        ArrayList<String> path = new ArrayList<String>();
        
        if(s == null){
            return result;
        }
        helper(s,result,path,0);
        
        return result;
    }
    
    private boolean isPalindrome(String s){
        int start = 0, end = s.length() - 1;
        while(start < end){
            if(s.charAt(start) != s.charAt(end)){
                return false;
            }
            start ++;
            end --;
        }
        return true;
    }
    
    private void helper(String s, ArrayList<ArrayList<String>> result,  ArrayList<String> path,int pos){
        
        if(pos == s.length()){
            result.add(new ArrayList<String>(path));
            return;
        }
        
        for(int i = pos + 1; i <= s.length(); i++){
            String prefix = s.substring(pos, i);
            if(!isPalindrome(prefix)){
                continue;
            }
            
            path.add(prefix);
            helper(s, result, path, i);
            path.remove(path.size() - 1);
        }
    }
}
```

---

- [prev: 135. Combination Sum](135-combination-sum.md)
- [next: 137. Clone Graph](137-clone-graph.md)
