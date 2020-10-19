# binary-search-tree-tutorial
A tutorial for working with binary trees using Javascript

[Repl example](https://repl.it/@webdevdave/pdxdavebinarysearchtree#main.js "Repl example")
<br />
[Step through example](http://www.pythontutor.com/live.html#code=class%20Node%20%7B%0A%20%20%20%20%20constructor%28value%29%7B%0A%20%20%20%20%20%20%20%20%20this.value%20%3D%20value%3B%0A%20%20%20%20%20%20%20%20%20this.left%20%3D%20null%3B%0A%20%20%20%20%20%20%20%20%20this.right%20%3D%20null%3B%0A%20%20%20%20%20%7D%0A%20%7D%0A%0A%20class%20BinarySearchTree%20%7B%0A%20%20%20%20constructor%28value%29%7B%0A%20%20%20%20%20%20%20%20this.root%20%3D%20new%20Node%28value%29%3B%0A%20%20%20%20%20%20%20%20this.count%20%3D%201%3B%0A%20%20%20%20%7D%0A%0A%20%20%20%20insertNumber%28value%29%7B%0A%20%20%20%20%20%20%20%20let%20newNode%20%3D%20new%20Node%28value%29%3B%0A%20%20%20%20%20%20%20%20this.count%2B%2B%3B%0A%0A%20%20%20%20%20%20%20%20const%20treeSearch%20%3D%20node%20%3D%3E%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20if%28value%20%3C%20node.value%29%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20if%28!node.left%29%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20node.left%20%3D%20newNode%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%20else%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20searchTree%28node.left%29%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20else%20if%20%28value%20%3E%20node.value%29%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20if%28!node.right%29%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20node.right%20%3D%20newNode%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%20else%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20searchTree%28node.right%29%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%7D%20//%20end%20of%20treeSearch%0A%20%20%20%20%20%20treeSearch%28this.root%29%0A%20%20%20%20%7D%20//%20end%20of%20insertNumber%0A%7D%20//%20end%20of%20BinearySearchTree%0A%0Aconst%20test%20%3D%20new%20BinarySearchTree%2810%29%3B%0Atest.insertNumber%285%29%3B%0Atest.insertNumber%2811%29%0A%0Atest&cumulative=false&curInstr=38&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false "Pythontutor")

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
 sides branches null. So if the number is 5, it'll look
 like this.

 ```
    5
   / \
 ```
Our class Node
 ```
 class Node {
     constructor(value){
         this.value = value;
         this.left = null;
         this.right = null;
     }
 }
```

Next we'll make another class called ```BinarySearchTree```. This will run 
various searches against the tree.  Notice that it too has a constructor. 
It'll take in a value we will call the root, and keep count of
the nodes.

```
class BinarySearchTree {
    constructor(value){
        this.root = new Node(value);
        this.count = 1;
    }
}

```
Inside of this class we will run our first method.  This will
insert numbers into the tree.  We'll call this ```insertNumber```.
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
values in the tree. The process is actually pretty simple.  First it will check
to see if the new incoming value is greater or less than the root node.  If less,
we proceed left.  If greater, we proceed right. If there is no number to the right
or left of the root node, we'll place the new income number.  If there is a number,
we will use recursion to keep drilling down to the right or left side of the tree
until the right place is located to place the number.

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

const test = new BinarySearchTree(10);
test.insertNumber(5);
test.insertNumber(11)

test
```

### FIND MIN AND MAX NUMBERS

[Repl example](https://repl.it/@webdevdave/minimum-and-maximum#main.js "Repl example")
<br />
[Step through example](http://pythontutor.com/visualize.html#code=class%20Node%20%7B%0A%20%20%20%20%20constructor%28value%29%7B%0A%20%20%20%20%20%20%20%20%20this.value%20%3D%20value%3B%0A%20%20%20%20%20%20%20%20%20this.left%20%3D%20null%3B%0A%20%20%20%20%20%20%20%20%20this.right%20%3D%20null%3B%0A%20%20%20%20%20%7D%0A%20%7D%0A%0A%20class%20BinarySearchTree%20%7B%0A%20%20%20%20constructor%28value%29%7B%0A%20%20%20%20%20%20%20%20this.root%20%3D%20new%20Node%28value%29%3B%0A%20%20%20%20%20%20%20%20this.count%20%3D%201%3B%0A%20%20%20%20%7D%0A%0A%20%20%20%20insertNumber%28value%29%7B%0A%20%20%20%20%20%20%20%20let%20newNode%20%3D%20new%20Node%28value%29%3B%0A%20%20%20%20%20%20%20%20this.count%2B%2B%3B%0A%0A%20%20%20%20%20%20%20%20const%20treeSearch%20%3D%20node%20%3D%3E%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20if%28value%20%3C%20node.value%29%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20if%28!node.left%29%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20node.left%20%3D%20newNode%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%20else%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20treeSearch%28node.left%29%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20else%20if%20%28value%20%3E%20node.value%29%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20if%28!node.right%29%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20node.right%20%3D%20newNode%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%20else%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20treeSearch%28node.right%29%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%7D%20//%20end%20of%20treeSearch%0A%20%20%20%20%20%20treeSearch%28this.root%29%0A%20%20%20%20%7D%20//%20end%20of%20insertNumber%0A%0A%0A%20%20%20%20minimum%28%29%20%7B%0A%20%20%20%20%20%20%20%20let%20currNode%20%3D%20this.root%3B%0A%20%20%20%20%20%20%20%20while%28currNode.left%29%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20currNode%20%3D%20currNode.left%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20return%20currNode.value%0A%20%20%20%20%7D%0A%0A%20%20%20%20maximum%28%29%7B%0A%20%20%20%20%20%20%20%20let%20currNode%20%3D%20this.root%3B%0A%20%20%20%20%20%20%20%20while%28currNode.right%29%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20currNode%20%3D%20currNode.right%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20return%20currNode.value%0A%20%20%20%20%7D%0A%0A%0A%0A%7D%20//%20end%20of%20BinearySearchTree%0A%0Aconst%20test%20%3D%20new%20BinarySearchTree%2827%29%3B%0Atest.insertNumber%2819%29%3B%0Atest.insertNumber%2831%29%3B%0Atest.insertNumber%2821%29%3B%0Atest.insertNumber%2834%29%3B%0Atest.insertNumber%2815%29%3B%0Atest.insertNumber%2828%29%3B%0Aconsole.log%28'min%20number',%20test.minimum%28%29%29%0Aconsole.log%28'max%20number',%20test.maximum%28%29%29%3B%0A%0A%0Atest%3B&cumulative=false&heapPrimitives=nevernest&mode=edit&origin=opt-frontend.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)

Since we know the numbers to the left of the root are
less than the root number, and greater to the right,
all we need to do is drill down to the right or left side
depending what we're looking for.  I'm going to take the code
from above, add a few more test numbers, then write in
the min and max methods.  The tree will look like this.

```
      27
    /   \
  19     31
  / \   / \
15  21 28  34
 ```


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


    minimum() {
        let currNode = this.root;
        while(currNode.left){
            currNode = currNode.left
        }
        return currNode.value
    }

    maximum(){
        let currNode = this.root;
        while(currNode.right){
            currNode = currNode.right
        }
        return currNode.value
    }



} // end of BinearySearchTree

const test = new BinarySearchTree(27);
test.insertNumber(19);
test.insertNumber(31);
test.insertNumber(21);
test.insertNumber(34);
test.insertNumber(15);
test.insertNumber(28);
console.log(test.minimum());
console.log(text.maximum());


test
```

