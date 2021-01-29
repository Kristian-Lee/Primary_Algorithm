## [141.环形链表](https://leetcode-cn.com/leetbook/read/top-interview-questions-easy/xnwzei/)

给定一个链表，判断链表中是否有环。如果链表中存在环，则返回 true 。 否则，返回 false 。

解题思路 ：

> 1. 用哈希表（Set集合）存放节点，当存入到相同的节点时，即链表有环。
> 2. 设置两个快慢指针，slow指针每次走一步，fast每次走两步，当slow等于fast时，说明链表有环。
>
> ```java
> public boolean hasCycle(ListNode head) {
>     ListNode fast = head, slow = head;
>     while (fast != null && fast.next != null) {
>         slow = slow.next;
>         fast = fast.next.next;
>         if (slow == fast) {
>             return true;
>         }
>     }
>     return false;
> }
> ```



## [104.二叉树的最大深度](https://leetcode-cn.com/leetbook/read/top-interview-questions-easy/xnd69e/)

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



## [98.验证二叉搜索树](https://leetcode-cn.com/leetbook/read/top-interview-questions-easy/xn08xg/)

给定一个二叉树，判断其是否是一个有效的二叉搜索树。

假设一个二叉搜索树具有如下特征：

- 节点的左子树只包含小于当前节点的数。
- 节点的右子树只包含大于当前节点的数。
- 所有左子树和右子树自身必须也是二叉搜索树。

解题思路：

> 通过递归实现。每层判断左孩子节点是否小于双亲节点，右孩子节点是否大于双亲节点。需要注意的时双亲节点对其孩子节点的孩子节点的大小范围也有限制。
>
> ```java
> public boolean isValidBST(TreeNode root) {
> 	return check(root, null, null);
> }
> public boolean check(TreeNode root, Integer min, Integer max) {
>     if (root == null) {
>         return true;
>     }
>     if (max != null && root.val >= max) {
>         return false;
>     }
>     if (min != null && root.val <= min) {
>         return false;
>     }
>     if (check(root.right, root.val, max) && check(root.left, min, root.val)) {
>         return true;
>     }
>     return false;
> }
> ```
>
> 

