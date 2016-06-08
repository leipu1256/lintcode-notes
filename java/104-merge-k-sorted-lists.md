[104. Merge k Sorted Lists](http://www.lintcode.com/problem/merge-k-sorted-lists)

- [prev: 103. Linked List Cycle II](103-linked-list-cycle-ii.md)
- [next: 105. Copy List with Random Pointer](105-copy-list-with-random-pointer.md)

---

put your own notes and solutions here.
you can add any reference link such as [title](reference url) here.


```
/**
 * Definition for ListNode.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int val) {
 *         this.val = val;
 *         this.next = null;
 *     }
 * }
 */ 
public class Solution {
    /**
     * @param lists: a list of ListNode
     * @return: The head of one sorted list.
     */
    private Comparator<ListNode> compare = new Comparator<ListNode>(){//定义接口
        public int compare(ListNode left, ListNode right){
            return left.val - right.val;
        }
    };
     
    public ListNode mergeKLists(List<ListNode> lists) {  
        // write your code here
        
        if(lists == null || lists.size() == 0){
            return null;
        }
        
        Queue<ListNode> heap = new PriorityQueue(lists.size(), compare);
        
        for(int i = 0; i < lists.size(); i++){
            if(lists.get(i) != null){//判断不为空
                heap.add(lists.get(i));
            }
        }
        
        ListNode dummy = new ListNode(0);
        ListNode tail = dummy;
        while(!heap.isEmpty()){//while(heap != null)这种写法错误！！
            ListNode head = heap.poll();
            if(head.next != null){
                heap.add(head.next);//判断head.next!= nul
            }
            tail.next = head;
            tail = tail.next;
        }
        return dummy.next;
        
    }
}

```
---

- [prev: 103. Linked List Cycle II](103-linked-list-cycle-ii.md)
- [next: 105. Copy List with Random Pointer](105-copy-list-with-random-pointer.md)
