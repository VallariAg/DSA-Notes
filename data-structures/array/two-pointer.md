# Two Pointer

_Pointers_ when solving two-pointer questions:

1. Items in the list must be in sorted order. So the array should be already-sorted or the question should not be asking for index (i.e. you can sort to find the answer values)
2. Usually I use `while pointer2 < pointer1` to loop through the array
3. Two-pointers generally decrease the space complexity to `O(1)`



Classic Problems:

1. 2Sum
2.  3Sum:&#x20;

    Problem: Find all 3-number subsets in array where a+b+c=0

    Solution: Loop through array for a + do 2Sum for b and c
