# binary-search-tree-tutorial
A tutorial for working with binary trees using Javascript


Binary search trees are fast for insertion, deletion and accessing elements
```
      5
    /   \
   3     7
  / \   / \
 1   4 6   9
 ```
 In this example, the root node is 5.  If we want to add a number,
 we first must determine if the number is less than or greater than
 the number 5.  If less, as in the case of 3, the number goes left. 
 If greater, the number goes right, as in the case of 7. The same
 rule applies for additional numbers.  For instance, the numeber 4
 is less than 5, so it goes left.  It's greater than 3 though, so it
 branches to the right after the number 3.  
 