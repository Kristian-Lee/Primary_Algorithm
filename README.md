## [环形链表](https://leetcode-cn.com/leetbook/read/top-interview-questions-easy/xnwzei/)

给定一个链表，判断链表中是否有环。如果链表中存在环，则返回 true 。 否则，返回 false 。

解题思路 ：

> 1. 用哈希表（Set集合）存放节点，当存入到相同的节点时，即链表有环。
>
> 2. 设置两个快慢指针，slow指针每次走一步，fast每次走两步，当slow等于fast时，说明链表有环。
>
>    ```java
>    public boolean hasCycle(ListNode head) {
>        ListNode fast = head, slow = head;
>        while (fast != null && fast.next != null) {
>            slow = slow.next;
>            fast = fast.next.next;
>            if (slow == fast) {
>                return true;
>            }
>        }
>        return false;
>    }
>    ```



## 二叉树的最大深度

给定一个二叉树，找出其最大深度。二叉树的深度为根节点到最远叶子节点的最长路径上的节点数。

解题思路：

> 很自然想到递归实现。递归计算出其左子树和右子树的最大深度，选出最大值并加1返回给上一层，当递归到达叶子节点的子节点时结束递归。
>
> ```java
> public int maxDepth(TreeNode root) {
>     if (root == null) {
>         return 0;
>     }
>     return Math.max(maxDepth(root.left), maxDepth(root.right)) + 1;
> }
> ```



