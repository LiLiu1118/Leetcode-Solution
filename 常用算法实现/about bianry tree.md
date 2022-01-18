#  二叉树遍历
![tree](https://github.com/LiLiu1118/Leetcode-Solution/blob/main/Markdown%20Photos/tree12.gif)

Depth First Traversals: 
(a) Inorder (Left, Root, Right) : 4 2 5 1 3 
(b) Preorder (Root, Left, Right) : 1 2 4 5 3 
(c) Postorder (Left, Right, Root) : 4 5 2 3 1

Breadth-First or Level Order Traversal: 1 2 3 4 5 
![Breadth-First](https://www.geeksforgeeks.org/level-order-tree-traversal/)

# 思路

无需设置min_prices,只要后一个数大于前一个数,就把差值累加起来,因为要利用到每一个valley以达到利润最大化.
