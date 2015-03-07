# BPlusTreeImplementation 

>**Author: Jingyi Chen**	
>**jc2834@cornell.edu**

###Coding logic:
* **SEARCH:**

Use a search helper to locate the key recursively.
Use binary search to speed up.

* **INSERT:**

Use a recursive insertHelper to locate the insert point, do insertion. If an overflow is detected, do split, newChildEntry contains information for continuous insertion. When newChildEntry is null, insertion process is terminated.

For handling leaf overflow, after splitting, leaf contains D entries, the rest entries is moves to a new leaf node for newChidEntry, since leaf node is a double-linked list, the linked-list's properties should update as well.

For handling index overflow, first D key values and D+1 node pointers(children) stay,last D keys and D+1 node pointers(children) move to new node for newChildEntry.

* **DELETE:**

Use a recursive deleteHelper to locate the delete point, do deletion. If an underflow is detected:

For leaf node underflow, get a sibling as instruction described. If the total key size of this leaf node and its sibling is less than or equal to twice the depth, merge them to one node, return the index for parent node processing correspondingly(oldChidEntry for further deletion). Otherwise, redistribute 2 nodes, with the smaller node contains "depth" number of keys eventually.

For index node underflow, get a sibling as instruction described. If the total key size of this index node and its sibling is less than twice the depth, merge them to one node, return the index for parent node processing correspondingly(oldChidEntry for further deletion). Otherwise, redistribute 2 nodes, with the smaller node contains "depth" number of keys eventually.

Deletion is terminated when oldChidEntry is null.

