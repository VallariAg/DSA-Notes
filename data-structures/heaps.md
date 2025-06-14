# Heaps

**Complete binary tree** (all levels filled except lowest + add leaf element at left most) that satisfy **heap property** (for all nodes either parent >= child or parent <= child).&#x20;

Two types of heap: **Min-heap** (root/heap\[0] is smallest) and **Max-heap** (root/heap\[0] is largest)

#### Array representation of heap tree

![](<../.gitbook/assets/image (8).png>)

Written in pre-order traversal (root -> left -> right). So for every node at index `i` in array

* index of left child is given by `2i + 1` and the right child is given by `2i + 2`&#x20;
* parent of `i` is given by `(i - 1) / 2`&#x20;
* last non-leaf node (i.e. last node with children) is given by `(i // 2) - 1`

![](<../.gitbook/assets/image (1).png>)

&#x20;

Why use heaps?

* Largest/smaller number accessible with O(1)
* Fast insertion/deletion with O(log n)
* Use cases:
  * Heap sort
  * Priority queue
* Heaps are basically an array which is heap-sorted. Or say heap sort algorithm uses heap DS. (TODO: review what is heap sort)
* Heaps are kind of sorted arrays such that the whole array is not sorted but with fast insertion/deletion and fast fetch of max/min. In a sorted array, fast min/max is possible but insertion/deletion is slower (basically add and re-sort).
* Question types:
  * "K th" largest/smallest
  * Questions which can be solved by sorting. Heaps would give a faster solution (if possible). &#x20;

### Implementation

In both implementations, we do not use Tree DS to solve it (tree is used to only visualize mentally). It is purely implemented in arrays, and above calculations are used to process left/right node or parent node.&#x20;

#### 1. Raw Implimentation: [https://www.programiz.com/dsa/heap-data-structure](https://www.programiz.com/dsa/heap-data-structure)

Time complexity:

* Heapify (convert binary tree -> heap, assuming part of tree is already heap): **O(log n)**
  * Heap up: swap `current` with `parent`, then `parent` with `grandparent`
  * Heap down: swap `current` with a `child`, then `child` with `grandchild`
* Build heap (unsorted array -> heap sort): **O (n)**&#x20;
  * consider leaf nodes are already heaps, heapify all other nodes from `last_non_leaf` node
* Heappush: **O(log n)**
  * Method: add at end -> heapify UP from there
* Heappop: **O(log n)**
  * Method: heapdelete with index=0
* Heapdelete (any element): **O (log n)**
  * Method:  swap `index` with last leaf -> remove new last -> heapify DOWN from `index`

```python
class KthLargest:

    def __init__(self, k: int, nums: List[int]):
        self.nums = []
        self.k = k
        if nums:
            self.nums = self.build_heap(nums)
            while len(self.nums) > k:
                self.heappop(self.nums)

    def add(self, val: int) -> int:
        # question specific
        if len(self.nums) < self.k:
            self.heappush(self.nums, val)
        elif val > self.nums[0]:
            self.heappush(self.nums, val)
            self.heappop(self.nums)
        return self.nums[0]
    
    def heappush(self, nums, val): # O(log n)
        # add at end -> heapify UP from there
        nums.append(val)
        
        self.min_heapify_up(nums, len(nums)-1)
        # self.max_heapify_up(nums, len(nums)-1)

    def heappop(self, nums):  # O (log n)
        self.remove(nums, 0)

    def remove(self, nums, index): # O (log n)
        # swap index with last leaf -> remove last -> heapify DOWN from index
        nums[index], nums[-1] = nums[-1], nums[index]
        nums.pop() 

        self.min_heapify(nums, index)
        # self.max_heapify(index)


    # build max heap from unsorted array
    def build_heap(self, nums): # O(n)
        last_non_leaf = (len(nums) // 2) - 1   # this is starting point, because leaf nodes are already heaps
        for i in range(last_non_leaf, -1, -1):
            self.min_heapify(nums, i)        # build min heap
            # self.max_heapify(nums, i)      # build max heap
        return nums

    # heapify tree under current 
    def max_heapify(self, nums, current): # O(log n)
        largest = current

        left = (2*current) + 1 
        right = (2*current) + 2
        if len(nums) > left and nums[largest] < nums[left]:   # (left index exists) and (left larger) 
            largest = left
        if len(nums) > right and nums[largest] < nums[right]:
            largest = right
        
        if largest != current:
            nums[largest], nums[current] = nums[current], nums[largest]
            self.max_heapify(nums, largest) # flow down this change to rest half of the tree under this
    
    # heapify tree under current
    def min_heapify(self, nums, current): # O(log n)
        smallest = current

        left = (2*current) + 1 
        right = (2*current) + 2
        if len(nums) > left and nums[smallest] > nums[left]:   # (left index exists) and (left smaller) 
            smallest = left
        if len(nums) > right and nums[smallest] > nums[right]:
            smallest = right
        
        if smallest != current:
            nums[smallest], nums[current] = nums[current], nums[smallest]
            self.min_heapify(nums, smallest) # flow down this change to rest half of the tree under this
        
    # heapify tree above current
    def min_heapify_up(self, nums, current):  # O (log n)
        while current > 0:
            parent = (current-1) // 2
            if nums[parent] > nums[current]:
                nums[parent], nums[current] = nums[current], nums[parent]
                current = parent
            else:
                break

    # heapify tree above current
    def max_heapify_up(self, nums, current):  # O (log n)
        while current > 0:
            parent = (current-1) // 2
            if nums[parent] < nums[current]:
                nums[parent], nums[current] = nums[current], nums[parent]
                current = parent
            else:
                break


```

[https://leetcode.com/problems/kth-largest-element-in-a-stream/](https://leetcode.com/problems/kth-largest-element-in-a-stream/)

#### 2. Implimentation using heapq

heapq in python: follow **zero based indexing** and implements **min-heap**

* `heap[0]` is the smallest item
* `heap.sort()` maintains the heap invariant!

Basic Functions:

* `heapq.heapify(list)` - O(n) in an array. Each individual call to heapify can take O(logn).
* `heapq.heappush`(_heap_, _item_) - O(log n)
* `heapq.heappop`(_heap_)   - O(log n) - returns smallest&#x20;
* `heapq.nlargest`(_n_, _iterable_, _key=None_)
* `heapq.nsmallest`(_n_, _iterable_, _key=None_)

\---&#x20;

heapq impliments MinHeap by default, to impliment MaxHeap:

```python
class MaxHeap: 
    def __init__(self, array = []):
        self.heap = array
        self.heapify()
        
    def heapify(self):
        self.heap = list(map(lambda x: -x, self.heap))
        heapq.heapify(self.heap)

    def push(self, item):
        heapq.heappush(self.heap, -item)
        
    def pop(self): # returns largest
        popped = heapq.heappop(self.heap)
        return -popped
    
    def length(self):
        return len(self.heap)
```

### Resources

* `heapq` documentation: [https://docs.python.org/3/library/heapq.html](https://docs.python.org/3/library/heapq.html)

### Good questions on Heaps

* Basic: [https://leetcode.com/problems/kth-largest-element-in-a-stream/](https://leetcode.com/problems/kth-largest-element-in-a-stream/)
* Tricky: [https://leetcode.com/problems/task-scheduler/](https://leetcode.com/problems/task-scheduler/)
* Design twitter (good question because it teaches that, instead of adding ALL values and making a huge heap, we can add initial set of values to heap and then pop those and add more based on the popped value): [https://leetcode.com/problems/design-twitter/](https://leetcode.com/problems/design-twitter/)
* use your smarts: [https://leetcode.com/problems/find-median-from-data-stream/](https://leetcode.com/problems/find-median-from-data-stream/)
