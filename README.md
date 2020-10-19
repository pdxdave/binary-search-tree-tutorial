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
 In this example the root node is 5.  If we want to add a number,
 we first must determine if the number is less than or greater than
 the number 5.  If less, as in the case of 3, the number goes left. 
 If greater, the number goes right, as in the case of 7. The same
 rule applies for additional numbers.  For instance, the numeber 4
 is less than 5, so it goes left.  It's greater than 3 though, so it
 branches to the right after the number 3.  
 

 ### INSERT A NUMBER TO THE TREE

 To add a number to a tree we need to make a class that will create
 a node to hold a number.  Call it a node, a card, a domino, whatever. 
 It holds a new incoming number.  I think of it as a card (e.g., 2x3 note card).
 This card will take in the new number and will make both the left and right
 sides branches null.  There's nothing there.  So if the number is 5, it'll look
 like this.

 ```
    5
   / \
 ```

 ```
 class Node {
     constructor(value){
         this.value = value;
         this.left = null;
         this.right = null;
     }
 }
```

Next we'll make another class. This will run various searches
against the tree.  Notice that it too has a constructor. 
It'll take in a number we'll call the root and keep count of
the nodes.

```
class BinarySearchTree {
    constructor(value){
        this.root = new Node(value);
        this.count = 1;
    }
}

```
Inside of this class we will run our first method.  This will be to 
insert numbers to the tree.  We'll call this ```insertNumber```.
When ```insertNumber``` is called it will take the passed value,
pop up to the class Node and create a new card with the value, and
then proceed through the rest of the method.
```
class BinarySearchTree {
    constructor(value){
        this.root = new Node(value);
        this.count = 1;
    }

    insertNumber(value){
        let newNode = new Node(value);
        this.count++;
    }
}
```
So this is what we have so far...
```
class Node {
     constructor(value){
         this.value = value;
         this.left = null;
         this.right = null;
     }
 }

 class BinarySearchTree {
    constructor(value){
        this.root = new Node(value);
        this.count = 1;
    }

    insertNumber(value){
        let newNode = new Node(value);
        this.count++;
    }
}

```

Now we'll create a function inside of the ```insertNumber``` method and
it will run through the tree to determine where the number should be placed.
We'll call this ```treeSearch```.  It'll take in the value and compare it to
values in the tree.

```
class Node {
     constructor(value){
         this.value = value;
         this.left = null;
         this.right = null;
     }
 }

 class BinarySearchTree {
    constructor(value){
        this.root = new Node(value);
        this.count = 1;
    }

    insertNumber(value){
        let newNode = new Node(value);
        this.count++;

        const treeSearch = node => {
            if(value < node.value){
                if(!node.left){
                node.left = newNode;
                } else {
                searchTree(node.left);
                } 
            }
            else if (value > node.value){
                if(!node.right){
                node.right = newNode;
                } else {
                searchTree(node.right);
                }
            }
        } // end of treeSearch
      treeSearch(this.root)
    } // end of insertNumber
} // end of BinearySearchTree

```