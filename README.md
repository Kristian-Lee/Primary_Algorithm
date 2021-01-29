## [环形链表](https://leetcode-cn.com/leetbook/read/top-interview-questions-easy/xnwzei/)

给定一个链表，判断链表中是否有环。如果链表中存在环，则返回 true 。 否则返回 false 。

解题思路 ：

> 1. 用哈希表（Set集合）存放节点，当存入到相同的节点时，即链表有环。
>
> 2. 设置两个快慢指针，slow指针每次走一步，fast每次走两步，当slow等于fast时，说明链表有环。
>
>    ```java
>   public boolean hasCycle(ListNode head) {
>        ListNode fast = head, slow = head;
>       while (fast != null && fast.next != null) {
>            slow = slow.next;
>            fast = fast.next.next;
>            if (slow == fast) {
>                return true;
>            }
>        }
>        return false;
>    }
>    ```

