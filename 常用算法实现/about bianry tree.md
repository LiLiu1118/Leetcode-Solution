#  二叉树遍历
![tree](https://github.com/LiLiu1118/Leetcode-Solution/blob/main/Markdown%20Photos/%E5%BF%AB%E9%80%9F%E6%8E%92%E5%BA%8F.gif)
Depth First Traversals: 
(a) Inorder (Left, Root, Right) : 4 2 5 1 3 
(b) Preorder (Root, Left, Right) : 1 2 4 5 3 
(c) Postorder (Left, Right, Root) : 4 5 2 3 1

Breadth-First or Level Order Traversal: 1 2 3 4 5 

# 思路

无需设置min_prices,只要后一个数大于前一个数,就把差值累加起来,因为要利用到每一个valley以达到利润最大化.
