### [LC102 ](https://leetcode.com/problems/binary-tree-level-order-traversal/)

BFS, Tree

NineChap template:
```java
class Solution {
   public List<List<Integer>> levelOrder(TreeNode root) {
       
       List<List<Integer>> res = new ArrayList();
       
       if (root == null) {
           return new ArrayList();
       }
       
       
       Queue<TreeNode> queue = new LinkedList();
       queue.offer(root);

       while(!queue.isEmpty()) {
           List<Integer> level = new ArrayList<Integer>();
           int size = queue.size();
           for (int i = 0; i < size; i++){
               TreeNode head = queue.poll();
               level.add(head.val);
               if(head.left != null){
                   queue.offer(head.left);
               }
               if(head.right != null){
                   queue.offer(head.right);
               }

           }
           res.add(level);
       }
       
       return res;
   }
}
```


Another solution using dummy node in discussions:
```java
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        if (root == null) {
            return new ArrayList();
        }
        
        List<List<Integer>> res = new ArrayList();
        
        Queue<TreeNode> q = new LinkedList();
        List<Integer> z = new ArrayList();
        q.add(root); q.add(null);
        while(!q.isEmpty()) {
            TreeNode t = q.poll();
            if(t == null && q.isEmpty()) {
                if(z.size() !=0)
                    res.add(z);
                continue;
            }
            if(t == null && !q.isEmpty()) {
                q.add(null);
                //stem.out.println();
                res.add(z);
                z = new ArrayList();
            }
            else { 
                z.add(t.val);
                if(t.left != null) {
                    q.add(t.left);
                }
                if(t.right != null) {
                    q.add(t.right);
                }
            }
        }
        
        return res;
    }
}
```