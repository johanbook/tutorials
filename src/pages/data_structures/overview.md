# Data structures

Here are some useful data structures.

## Array list

An array list is a data structure where one continuous sequence of memory is
allocated. This allows for quickly retrieving data at a given index, but data
insertion and appending is slow. There are dynamic array lists that
automatically reallocates memory if the array list risks growing beyond its
initial bounds.

**Usage**: Ordering matters and items are expected to be read more often then
they are changed.

| Operation      | Time complexity | Note                                                 |
| :------------- | :-------------- | :--------------------------------------------------- |
| Random access  | O(1)            |                                                      |
| Appending item | O(1)            | Typically O(1) but list might need to be reallocated |
| Deleting item  | O(n)            |                                                      |

## Linked list

A linked list consists of several nodes that have a reference to each other.
This makes it quick to delete and insert items, but retrieving by index is slow.

A linked list can be single linked (one can only iterate it one direction) or
double linked (it is bidirectional).

**Usage**: Ordering matters and items are expected to be changed more often then
they are read.

| Operation      | Time complexity | Note                                                            |
| :------------- | :-------------- | :-------------------------------------------------------------- |
| Random access  | O(n)            | Might require iterating through all nodes                       |
| Appending item | O(1)            | If one maintains reference to last item, otherwise O(n)         |
| Deleting item  | O(1)            | Given a reference to the item, deletion is a constant operation |

## Stacks

A stacks is a type of an ordered structure where one is intended to only access
the list item. This is called LIFO (Last In First Out). It can easily be
implemented using an array list but appending would then be O(n) in worst case.
Instead one can use a singly linked list where appending is done to first
position in list.

| Operation | Time complexity | Note |
| :-------- | :-------------- | :--- |
| Popping   | O(1)            |      |
| Appending | O(1)            |      |

## Queues

Queues are similar to stacks but one instead accesses the first item making them
FIFO (First In First Out). For implementation, one should use the Dequeue data
structure, although one could also use a linked list which has constant
complexity in both popping and appending..

| Operation | Time complexity | Note |
| :-------- | :-------------- | :--- |
| Popping   | O(1)            |      |
| Appending | O(1)            |      |

## Hash table

A hash table is an array list where indexes are hashed in a modulus. This allows
one to use any hashable object as a index (often referred to key in this
context). If there are collisions at a given index, then one uses a linked list
as value. Hash table have excellent time complexity assuming uniformity in the
hash algorithm and a suitable sized preallocated memory.

In order words, a hash table is similar to a list but it does not have a concept
of order. Hence it is not very suitable for stacks or queues.

| Operation     | Time complexity | Note |
| :------------ | :-------------- | :--- |
| Random access | O(1)            |      |
| Deleting item | O(1)            |      |

## Read next

- [Graphs](graphs)
