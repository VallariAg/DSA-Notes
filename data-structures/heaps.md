# Heaps

**Complete binary tree** (add leaf element at left most) that satistify **heap property** (for all nodes either parent >= child or parent <= child).&#x20;

Two types of heap: **Min-heap** (root/heap\[0] is smallest) and **Max-heap** (root/heap\[0] is largest)

#### Array representation of heap tree

![](<../.gitbook/assets/image (8).png>)

Written in pre-order traversal (root -> left -> right). So for every node at index `i` in array

* index of left child is given by `2i + 1` and the right child is given by `2i + 2`&#x20;
* parent of `i` is given by `(i - 1) / 2`&#x20;

![](<../.gitbook/assets/image (1).png>)

&#x20;

Why use heaps?

* Largest/smaller number accessible at O(1)
* Fast insertion
* Priority queue
* Heaps are basically an array which is heap-sorted. Or say heap sort algorithm uses heap DS. (TODO: review what is heap sort)
* Heaps are kind of sorted arrays such that the whole array is not sorted but with fast insertion/deletion and fast fetch of max/min. In a sorted array, fast min/max is possible but insertion/deletion is slower (basically add and re-sort).&#x20;

#### 1. Raw Implimentation: [https://www.programiz.com/dsa/heap-data-structure](https://www.programiz.com/dsa/heap-data-structure)

heapify (convert binary tree -> heap):

```python
class KthLargest: 

    def __init__(self, k: int, nums: List[int]):
        self.nums = nums
        self.k = k
        # build a max heap
        self.nums = self.heapify(nums)

    def add(self, val: int) -> int:
        # question specfic function
        self.heappush(val)
        while len(self.nums) > self.k:
            self.heappop()
        return self.nums[0] # kth largest

    def heappush(self, val):
        # push and heapify
        self.nums.append(val)
        self.nums = self.heapify(self.nums)

    def heappop(self):
        # remove root and heapify
        if len(self.nums) < 0:
            return []
        self.nums = self.nums[1:]
        self.nums = self.heapify(self.nums)

    def heapify(self, nums):
        last_non_leaf = (len(nums) // 2) - 1
        for i in range(last_non_leaf, -1, -1):
            nums = self.min_heapify_current(nums, i)
            # nums = self.max_heapify_current(nums, i)
        return nums

    def max_heapify_current(self, nums, current):
        largest = current

        left = (2*current) + 1 
        right = (2*current) + 2
        if len(nums) > left and nums[largest] < nums[left]:   # (left index exists) and (left larger) 
            largest = left
        if len(nums) > right and nums[largest] < nums[right]:
            largest = right
        
        nums[largest], nums[current] = nums[current], nums[largest]
        return nums
    
    def min_heapify_current(self, nums, current):
        smallest = current

        left = (2*current) + 1 
        right = (2*current) + 2
        if len(nums) > left and nums[smallest] > nums[left]:   # (left index exists) and (left smaller) 
            smallest = left
        if len(nums) > right and nums[smallest] > nums[right]:
            smallest = right
        
        nums[smallest], nums[current] = nums[current], nums[smallest]
        return nums
        

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
