# Sorting

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

### Algorithms

#### Bubble Sort

Each element (biggest for ascending order) bubble up to end of array in each iteration.

```python
class Solution:
    def sortArray(self, nums: List[int]) -> List[int]:
        for i in range(len(nums)):
            for j in range(len(nums)-i-1):
                if nums[j+1] < nums[j]:
                    nums[j], nums[j+1] = nums[j+1], nums[j]
        return nums

```

#### Selection Sort

Selects the smallest element in each iteration and places that element at the beginning.

```python
class Solution:
    def sortArray(self, nums: List[int]) -> List[int]:
       for i in range(len(nums)):
            minindex = i
            for j in range(i+1, len(nums)):
                if nums[minindex] > nums[j]:
                    minindex = j
            nums[minindex], nums[i] = nums[i], nums[minindex]
        return nums

```

#### Insertion Sort

Places an unsorted element at its suitable place in each iteration.

```python
class Solution:
    def sortArray(self, nums: List[int]) -> List[int]:
        # more naturally understood sol, but does more swaps
        for i in range(1, len(nums)):
            key = nums[i]
            j = i - 1
            while (j>=0) and (key < nums[j]):
                nums[j+1], nums[j] = nums[j], nums[j+1]
                j -= 1
        return nums

class Solution:
    def sortArray(self, nums: List[int]) -> List[int]:
        # more efficent version of above
        for i in range(1, len(nums)):
            key = nums[i]
            j = i - 1
            while (j>=0) and (key < nums[j]):
                nums[j+1] = nums[j] # 
                j -= 1
            nums[j+1] = key
        return nums

```

#### Merge Sort

```
```

#### Quick Sort

```
```





### References&#x20;

* [https://www.bigocheatsheet.com/](https://www.bigocheatsheet.com/)
* [https://www.programiz.com/dsa/sorting-algorithm](https://www.programiz.com/dsa/sorting-algorithm)
