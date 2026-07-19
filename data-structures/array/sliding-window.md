# Sliding Window

Tell: When a questions asks for **"consecutive string/array"** or **"substring/sub-array"**,  it _could_ be that sliding window can work. Usually when the given order matters.&#x20;

Usually we need to track 4 things:

```
[1, 2, 3, 4, 5]
 ^     ^

globally:
sol = global var storing final solution
i or p1 = starting window 
j or p2 = window end 

locally (of each iteration):
new = newly added element in window
curr_sol = local variable with solution of that window

(other useful calcs):
window = s[i:j+1]
window_size = j - i + 1
```

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption><p><a href="https://leetcode.com/problems/longest-substring-without-repeating-characters/">https://leetcode.com/problems/longest-substring-without-repeating-characters/</a></p></figcaption></figure></div>

Basic format I use to solve all sliding window (2026):

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/Screenshot 2026-07-19 at 6.45.24 PM.png" alt="https://leetcode.com/problems/longest-repeating-character-replacement/"><figcaption><p><a href="https://leetcode.com/problems/longest-repeating-character-replacement/">https://leetcode.com/problems/longest-repeating-character-replacement/</a></p></figcaption></figure></div>



Tip 1: it can get really confusing with too many variables, so keep number of variables in check. I always get lost between window pointers.&#x20;

Tip 2 (July 2026): use `i` and `j` instead of `p1` and `p2` - somehow brain likes i and j better (probably familiarity) &#x20;

#### Two types of sliding window problems:&#x20;

1. Fixed size
2. Variable size

Practice queues by type: [https://leetcode.com/discuss/post/5886397/dsa-patterns-you-need-to-know-by-anubhav-x7og/](https://leetcode.com/discuss/post/5886397/dsa-patterns-you-need-to-know-by-anubhav-x7og/)

