#  二叉树遍历
![tree](https://github.com/LiLiu1118/Leetcode-Solution/blob/main/Markdown%20Photos/tree12.gif)

##  Depth First Traversals: 三种情况用递归方法都很近似的简单，但是迭代法的话后序遍历最复杂，因为在回退到父节点的时候不立即访问父节点，而是首先访问右儿子。

(a) Inorder (Left, Root, Right) : 4 2 5 1 3 (Leetcode 94)

(b) Preorder (Root, Left, Right) : 1 2 4 5 3 (Leetcode 144)

(c) Postorder (Left, Right, Root) : 4 5 2 3 1 (Leetcode 145) 

##  Breadth-First or Level Order Traversal: 1 2 3 4 5  (Leetcode 102)

[Breadth-First](https://www.geeksforgeeks.org/level-order-tree-traversal/)
