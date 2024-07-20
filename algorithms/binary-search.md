# Binary Search

Only works in **sorted arrays**.&#x20;

Binary Search is the **best method to use for searching in **_**sorted arrays**_ because it's the _fastest_ searching algorithm with O(log n), meanwhile brute force search is O(n).

**Time Complexities**

* **Best case complexity**: `O(1)`
* **Average case complexity**: `O(log n)`
* **Worst case complexity**: `O(log n)`

**Space Complexity -** `O(1)`

#### Interactive Method

<pre class="language-python"><code class="lang-python"><strong>class Solution:
</strong>    def iterative_binarys(self, nums: List[int], target: int):
        p1, p2 = 0, len(nums) - 1
        while(p2>=p1):
            mid = p1 + ((p2-p1) // 2)
            if target == nums[mid]:
                return mid
            elif target > nums[mid]:
                p1 = mid+1
            else:
                p2 = mid-1
        return -1
</code></pre>

#### Recursive Method

Follows [the divide and conquer](https://www.programiz.com/dsa/divide-and-conquer) approach.

```python
class Solution:
    def recursive_binarys(self, nums, target, left, right):
        if left > right:
            return -1
        mid = left + ((right - left) // 2)
        if nums[mid] == target:
            return mid
        elif nums[mid] > target:
            return self.recursive_binarys(nums, target, left, mid-1)
        else:
            return self.recursive_binarys(nums, target, mid+1, right)
```

Note: Do not worry if it's an even numbered arrays, `mid` will reach there (as it checks even 1 length array `[a]` at the end)

