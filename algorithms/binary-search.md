# Binary Search

Only works in **sorted arrays**.&#x20;

Binary Search is the **best method to use for searching in&#x20;**_**sorted arrays**_ because it's the _fastest_ searching algorithm with O(log n), meanwhile brute force search is O(n).

**Time Complexities**

* **Best case complexity**: `O(1)`
* **Average case complexity**: `O(log n)`
* **Worst case complexity**: `O(log n)`

**Space Complexity -** `O(1)`

***

#### Iterative Method

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

***

## Patterns

{% embed url="https://leetcode.com/discuss/post/7441588/binary-search-patterns-that-solve-80-of-qu83f/" %}

* Pattern 1: Classic Binary Search (Search an Element)
* Pattern 2: First / Last Occurrence (Duplicates)
* Pattern 3: Lower Bound / Upper Bound
* Pattern 4: Binary Search on Answer **(MOST IMPORTANT)**
* Pattern 5: Rotated Sorted Array \[IMPORTANT]&#x20;



#### \[IMP Pattern] Binary Search on Answer <a href="#pattern-3-lower-bound--upper-bound" id="pattern-3-lower-bound--upper-bound"></a>

Binary search on range of possible answers.&#x20;

Template:

<pre class="language-python"><code class="lang-python"><strong>   def valid_ans(self, k, piles, h):
</strong>        ans = 0
        for p in piles:
            ans += math.ceil(p / k)
            if ans > h:
                return False  # no answer
        return True

    def minEatingSpeed(self, piles: List[int], h: int) -> int:
        # binary search on answer 
        # (for possible answers range, see where condition fits)
        i, j = 1, max(piles)
        min_ans = j
        while i &#x3C;= j:
            mid = i + ((j - i) // 2)
            if self.valid_ans(mid, piles, h):
                min_ans = min(min_ans, mid)
                j = mid - 1
            else:
                i = mid + 1
        return min_ans
</code></pre>

Q: [https://leetcode.com/problems/koko-eating-bananas/](https://leetcode.com/problems/koko-eating-bananas/)&#x20;

#### \[IMP] Modified Binary Search

Applies to **rotated arrays**, unsorted arrays, or specialized conditions.

```python
```



More questions: [https://leetcode.com/discuss/post/5886397/dsa-patterns-you-need-to-know-by-anubhav-x7og/](https://leetcode.com/discuss/post/5886397/dsa-patterns-you-need-to-know-by-anubhav-x7og/)



