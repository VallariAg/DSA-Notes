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

Example:

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption><p><a href="https://leetcode.com/problems/longest-substring-without-repeating-characters/">https://leetcode.com/problems/longest-substring-without-repeating-characters/</a></p></figcaption></figure></div>

Tip 1: it can get really confusing with too many variables, so keep number of variables in check. I always get lost between window pointers.&#x20;

Tip 2 (July 2026): use `i` and `j` instead of `p1` and `p2` - somehow brain likes i and j better (probably familiarity) &#x20;

## Pattern

Two types of sliding window:

#### 1. Fixed sliding window

#### 2. Variable size template

Basic template:

```python
class Solution:
    def is_valid_substring(self, counter, k):
        max_ = max(counter.values())
        rest = sum(counter.values()) - max_
        return rest <= k

    def characterReplacement(self, s: str, k: int) -> int: # AABABBA, 1
        count = defaultdict(int)
        i = 0
        ans = 0
        for j in range(0, len(s)): # 0, 3, {'A': 3, 'B': 1}
            window = s[i:j+1] # AABA     (WINDOW)
            count[s[j]] += 1 
            while not self.is_valid_substring(count, k):
                count[s[i]] -= 1
                i += 1
            curr_ans = j - i + 1 # 4   (SIZE of WINDOW)
            ans = max(ans, curr_ans) # 4
        return ans
```

Q: [https://leetcode.com/problems/longest-repeating-character-replacement/](https://leetcode.com/problems/longest-repeating-character-replacement/)





Practice queues by type: [https://leetcode.com/discuss/post/5886397/dsa-patterns-you-need-to-know-by-anubhav-x7og/](https://leetcode.com/discuss/post/5886397/dsa-patterns-you-need-to-know-by-anubhav-x7og/)

