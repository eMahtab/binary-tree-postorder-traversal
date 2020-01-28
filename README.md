# Binary Tree Postorder Traversal 🌲
## https://leetcode.com/problems/binary-tree-postorder-traversal

Given a binary tree, return the postorder traversal of its nodes' values.
```
Example:

Input: [1,null,2,3]
   1
    \
     2
    /
   3

Output: [3,2,1]
```
**Follow up: Recursive solution is trivial, could you do it iteratively?**

# Postorder Traversal :
![Binary Tree](binary-tree.PNG?raw=true "Binary Tree")

Note that node 75 doesn't have left child and node 29 doesn't have right child.

The postorder traversal for above binary tree will be **[21, 20, 35, 30, 75, 67, 50, 29, 60, 65, 24, 43, 70]**

## Implementation : Recursive

```java
import java.util.ArrayList;
import java.util.List;

public class App {

     public static void main(String[] args) {
	   TreeNode root = new TreeNode(70);
           root.left = new TreeNode(67); root.right = new TreeNode(43);
		
	   root.left.left = new TreeNode(35); root.left.right = new TreeNode(75); 
		
           root.left.left.left = new TreeNode(21); root.left.left.right = new TreeNode(20);
		
           root.left.right.right = new TreeNode(30);
		
           root.right.left = new TreeNode(29); root.right.left.left = new TreeNode(50);
		
           root.right.right = new TreeNode(24); 
		
	   root.right.right.left = new TreeNode(60); root.right.right.right = new TreeNode(65);
           System.out.println(inorderTraversal(root));
     }
	
	
     // Definition for a binary tree node.
     static public class TreeNode {
	      int val;
	      TreeNode left;
	      TreeNode right;
	      TreeNode(int x) { val = x; }
     }
	 
	
     public static List <Integer> inorderTraversal(TreeNode root) {
        List <Integer> res = new ArrayList<Integer>();
        helper(root, res);
        return res;
     }

     public static void helper(TreeNode root, List <Integer> res) {
        if (root != null) {
            helper(root.left, res);
            helper(root.right, res);
            res.add(root.val);
        }
     }
}

```
## Implementation : Iterative (One Stack)

```java
public List<Integer> postorderTraversal(TreeNode root) {
      List<Integer> res = new ArrayList<>();
      if(root == null)
          return res;
      Stack<TreeNode> stack = new Stack<TreeNode>();
      stack.push(root);
      while(!stack.isEmpty()){
          TreeNode current = stack.pop();
          res.add(0,current.val);
          if(current.left != null){
              stack.push(current.left);
          }
          if(current.right != null){
              stack.push(current.right);
          }
      }  
   return res;  
}
```

## Implementation : Iterative (Two Stack)

```java
public List<Integer> postorderTraversal(TreeNode root) {
      List<Integer> res = new ArrayList<>();
      if(root == null)
          return res;
      Stack<TreeNode> stack = new Stack<TreeNode>();
      Stack<Integer> values = new Stack<>();  
      stack.push(root);
      while(!stack.isEmpty()){
          TreeNode current = stack.pop();
          values.push(current.val); 
          if(current.left != null){
              stack.push(current.left);
          }
          if(current.right != null){
              stack.push(current.right);
          }
      } 
      while(!values.isEmpty()){
          res.add(values.pop());
      }
      return res;  
}
```

# References :
1. https://www.youtube.com/watch?v=sMI4RBEZyZ4
2. https://www.techiedelight.com/postorder-tree-traversal-iterative-recursive
