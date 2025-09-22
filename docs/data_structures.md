# Data Structures

## Linked Lists

Linked lists are sets of entries that each point to the location of
the next entry, which allows for fast manipulations in the order of
the elements in exchange for a larger consumption of memory and a
slower iteration of all elements compared to traditional arrays.

### Double-linked Lists

Double-linked lists have entries that both point to the previous and
next value.

### Circular Linked Lists

Circular linked lists have the last element point back to the first
element to create a closed loop.

### Circular Double-linked Lists

The same can apply to double-linked lists, where both the last and
the first and the last element point to each other.

## Stacks

Stacks are lists of elements that works with the idea of
last-in-first-out in mind. Elements are "stacked" on top of each
other. The elements are then removed (or "popped") from the top.

## Queues

Queues follow the principle of first-in-first-out. The elements are
"pushed" in from behind and taken out at the front
("enqueue/dequeue").

## Hash Tables

Hash tables map their elements to a unique index using a hash
function which increases access times in large data sets.

For the hash function, there is no single right choice. Instead, it
is highly dependant on the precise use case.

### Hash Sets

Hash sets work in a similar fashion to hash tables. The difference is
that the hash function does not have to produce unique indices.
Instead, multiple elements can share the same index and are accessed
as a group.

### Hash Maps

Finally, hash maps make use of the same concepts as the hash set,
only the hashing does not take place on the whole data, but an
identifier instead, that is then used to access the data.

## Trees
### Binary Trees

Binary trees are data structures, that follow a tree-like build where
every node can have up to two child nodes (left/right).

There are several use cases, where the use of such a structure is
highly efficient.

#### Breadth First Search

There are to main methods of traversing a binary tree:

- Breadth First Search (BFS);
- and Depth First Search (DFS).

BFS starts with the root of the tree and iterates inwards until the
search criteria is satisfied.

On the contrary, DFS starts with the inner-most layer of the tree and
works through each layer to the root. For DFS, there are multiple
algorithms, that will be explained in the following sections.

#### Pre-order Traversal

Pre-order traversal simply runs the handler for every node's left and
right child recursively which prompts the handler to be run for every
node to the left-most leaf first, and then for every node of every
layer from left to right.

```python
def preOrderTraversal(node):
    if node is None:
        return
    print(node.data, end=", ")
    preOrderTraversal(node.left)
    preOrderTraversal(node.right)
```

#### In-order Traversal

In-order traversal first handles the left child-nodes recursively,
before handling the the parent node and lastly the right-hand child
nodes.

```python
def inOrderTraversal(node):
    if node is None:
        return
    inOrderTraversal(node.left)
    print(node.data, end=", ")
    inOrderTraversal(node.right)
```

#### Post-order Traversal

Post-order traversal first iterates through the child nodes before
going through the parents.

```python
def postOrderTraversal(node):
    if node is None:
        return
    postOrderTraversal(node.left)
    postOrderTraversal(node.right)
    print(node.data, end=", ")
```

#### Array Implementation

The array implementation of a binary tree is simple, yet not space
efficient if the tree has a lot of layers with barely any nodes.

The code snippet below provides one way of implementing a binary
tree.

```python
binary_tree_array = [
    'R', 'A', 'B', 'C', 'D', 'E', 'F',
    None, None, None, None, None, None, 'G'
]

def left_child_index(index):
    return 2 * index + 1

def right_child_index(index):
    return 2 * index + 2
```

### Binary Search Trees

A binary search is constructed in a way that results in an in-order
traversal to iterate through the value in an ascending order.

So, if the binary tree were to consist of numbers, every time a new
number is inserted, the new value is compared to the root node and
depending on whether the value is larger or smaller decides whether
the algorithm should continue on the left or the right.

This operation is repeated with every child node too until a leaf
node is found. Then, the value is inserted to the left or the right
of the leaf (after being compared).

### AVL Trees

AVL trees are, in essence, binary search trees. The key difference is
that it balances itself out, so that there is no more that one layer
of difference from each of the tree's sides. This minimizes the
tree's height.

This is done by keeping track of the imbalance of the branches of all
nodes. If any imbalance hits two layers of difference, the elements
are shifted so that the element with the imbalance is shifted to the
side with the lesser amount of layers.

