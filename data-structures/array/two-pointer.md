# Two Pointer

**Tell:**&#x20;

1. Items in the list must be in **sorted** orde&#x72;**.** The array should be already-sorted or the question should not be asking for index (i.e. you can sort to find the answer values)
2. If the problem asks for a **pair of values** or a result that can be generated from two values.

Implementation: How-to _Pointers_ when solving two-pointer questions:

1. Usually I use `while pointer2 < pointer1` to loop through the array
2. Two-pointers approach generally decrease the space complexity to `O(1)` - so try this on array questions when asked to use constant space.&#x20;



**Trick of solving the questions (what to practice):**&#x20;

1\) sort the array&#x20;

2\) sometimes (many times) its actually 3 pointer - (usually run a `for` loop for third pointer and solve two pointer)

3\) check where best to start pointers - (start+end OR start+start OR end+end)&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2026-07-03 at 1.36.03 PM.png" alt=""><figcaption></figcaption></figure>

[https://bytebytego.com/courses/coding-patterns/two-pointers/introduction-to-two-pointers](https://bytebytego.com/courses/coding-patterns/two-pointers/introduction-to-two-pointers)

**Classic Problems:**

1. 2Sum
2.  3Sum: [https://leetcode.com/problems/3sum/](https://leetcode.com/problems/3sum/)&#x20;

    Problem: Find all 3-number subsets in array where a+b+c=0

    Solution: Loop through array for a + do 2Sum for b and c
3.  Trapping rain water: [https://leetcode.com/problems/trapping-rain-water/](https://leetcode.com/problems/trapping-rain-water/)

    Don't try to solve it in O(1) space - it is a weird unique solution, solve in O(n) space first. &#x20;
4. Container with most water: [https://leetcode.com/problems/container-with-most-water/](https://leetcode.com/problems/container-with-most-water/)

Other problems:

* Valid Triangle: [https://leetcode.com/problems/valid-triangle-number/description/](https://leetcode.com/problems/valid-triangle-number/description/) - trick is where to start the pointers (start/end)
* [Bag of Tokens](https://leetcode.com/problems/bag-of-tokens/) - easy 2 pointer
* [Next Permutation](https://leetcode.com/problems/next-permutation/) - unique solution (it's okay if you can't do it yourself)
