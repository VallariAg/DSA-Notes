# Sliding Window

Tell: When a questions asks for **"consecutive string/array"** or **"substring/sub-array"**,  it _could_ be that sliding window can work.

Usually we need to track 4 things:

```
[1, 2, 3, 4, 5]
 ^     ^

globally:
sol = global var storing final solution
p1 = starting window
p2 = window end

locally (of each iteration):
new = newly added element in window
curr_sol = local variable with solution of that window

```

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption><p><a href="https://leetcode.com/problems/longest-substring-without-repeating-characters/">https://leetcode.com/problems/longest-substring-without-repeating-characters/</a></p></figcaption></figure>

Tip: it can get really confusing with too many variables, so keep number of variables in check. I always get lost between window pointers.&#x20;







