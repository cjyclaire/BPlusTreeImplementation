README

Author: Jingyi Chen	netID: jc2834
Author: Shaoke Xu	netID: sx77
----------------------------------
Coding logic:
----------------------------------
1. SEARCH:

Use a search helper to locate the key recusively.
Use binary search to speed up.

2. INSERT:

Use a recusive insertHelper to locate the insert point, do insertion. If an overflow is detetecd, do split, newChildEntry contains information for continuous insertion. When newChildEntry is null, insertion process is terminated.

For handling leaf overflow, after splitting, leaf contains D entries, the rest entries is moves to a new leaf node for newChidEntry, since leaf node is a doublelinked list, the linkedlist's properties should update as well.

For handling index overflow, first D key values and D+1 node pointers(children) stay,last D keys and D+1 node pointers(children) move to new node for newChildEntry.

3. DELETE:

Use a recusive deleteHelper to locate the delete point, do deletion. If an underflow is detected:

For leaf node underflow, get a sibling as instruction described. If the total key size of this leaf node and its sibling is less than or equal to twice the depth, merge them to one node, return the index for parentnode processing correspondingly(oldChidEntry). Otherwise, redistribute 2 nodes, with the smaller node contains "depth" number of keys eventually.

For index node underflow, get a sibling as instruction described. If the total key size of this index node and its sibling is less than twice the depth, merge them to one node, return the index for parentnode processing correspondingly(oldChidEntry). Otherwise, redistribute 2 nodes, with the smaller node contains "depth" number of keys eventually.

Deletion is terminated when oldChidEntry is null.

----------------------------------
Bugs:
----------------------------------
None

