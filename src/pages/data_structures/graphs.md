# Graphs

A graph consist of several nodes which are linked to each other by references,
similar to a linked list except each node might be connected to several other
nodes.

## Types

- **Binary tree**. Tree where each node has two children or none.
- **Quadtree**. Tree where each node has four children or none. Can be used to
  index 2d spatial data.

## Binary search tree

A binary search tree is a graph where each node has a left and a right node.
When data is feed down the tree a binary operation is done in each node to
determine if it is fed left or right.

### Tree traversal

When needs to be able effectively traverse the tree. This is often done
recursively but will then give rise to a call stack that increases the space
complexity of the algorithm.

Some approaches

- **Inorder traversal**. First visit left subtree, then root node and finally
  right subtree.
- **Preorder traversal**. First visit root node then left subtree and finally
  right subtree.
- **Postorder traversal**. First visit left subtree, then right subtree and
  finally root node.
