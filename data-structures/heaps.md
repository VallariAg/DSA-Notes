# Heaps

**Complete binary tree** (add leaf element at left most) that satistify **heap property** (for all nodes either parent >= child or parent <= child).&#x20;

Two types of heap: **Min-heap** (root/heap\[0] is smallest) and **Max-heap** (root/heap\[0] is largest)

For array representation of heap tree, for every node at index `i` in array:

* index of left child is given by `2i + 1` and the right child is given by `2i + 2`
* parent of `i` is given by `(i - 1) / 2`

``![](<../.gitbook/assets/image (1).png>)``

&#x20;

#### 1. Raw Implimentation: [https://www.programiz.com/dsa/heap-data-structure](https://www.programiz.com/dsa/heap-data-structure)

#### 2. Implimentation using heapq

heapq in python: follow **zero based indexing** and implements **min-heap**

* `heap[0]` is the smallest item
* `heap.sort()` maintains the heap invariant!

Basic Functions:

* `heapq.heapify(list)`
* `heapq.heappush`(_heap_, _item_)
* `heapq.heappop`(_heap_)
* `heapq.nlargest`(_n_, _iterable_, _key=None_)
* `heapq.nsmallest`(_n_, _iterable_, _key=None_)



### Resources

* `heapq` documentation: [https://docs.python.org/3/library/heapq.html](https://docs.python.org/3/library/heapq.html)
