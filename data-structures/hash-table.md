---
description: Dict in python!
---

# Hash Table



Helpful Libraries:

* [defaultdict](https://docs.python.org/3/library/collections.html#collections.defaultdict) from collections

```python
from collections import defaultdict

d = {}
print(d["car"]) # KEY ERROR!

dd = defaultdict(list)
print(dd["car"]) # []
```

* [Counter](https://docs.python.org/3/library/collections.html#collections.Counter) from collections

```python
from collections import Counter

c = Counter(['eggs', 'ham', 'eggs', 'eggs', 'ham', 'bread'])
# c = { 'eggs': 3, 'ham': 2, 'bread': 1 }

c['bacon']       # 0  (count of a missing element is zero)
c.most_common(2) # [('eggs', 3), ('ham', 2)]
c.values()
c.keys()
```

## Questions

1. [https://leetcode.com/problems/task-scheduler/](https://leetcode.com/problems/task-scheduler/)

Use Counter and sort the answer keeping the most frequent in mind. Logic!

