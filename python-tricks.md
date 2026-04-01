# Python Tricks

### String

<pre class="language-python"><code class="lang-python"><strong>ord(char) - ord('a')  
</strong>>>> ord('a') = 97
>>> ord('A') = 65
>>> ord('z') = 97+25 = 122 # total 26 letters calculations
>>> ord('Z') = 65+25 = 90  # total 26 letters calculations

</code></pre>

### Array

```python
array = [1, 1, 1, 3]

array.count(1) # 3
array.find(1) # 0 
array.rfind(1) # 2
array.find(2) # -1 
```

### Dict

```python
d ={}
d.get('cat', 0) # 0 - setting default if key doesn't exist
```

```python
from collections import defaultdict

d = defaultdict(int) # (dict, but if key doesn't exist then create one with some default value)
d['cat'] # 0
```

### Set

```python
val in set1           # O(1) operation  
set([1,2]) - set([1]) = set([2])  # substraction

```

### Tuple

ordered + immutable collection of items

```python
dict[tuple(1,2,3)] = 2      # hashable: can be used as dict key
```

#### Float

```python
float('inf')
float('-inf')
```

#### Math

```python
import math

math.ceil(2.2) # 3
math.floor(2.8) # 2
```

### Libraries&#x20;

* `defaultdict` (dict, but if key doesn't exist then create one with some default value)
* `dequeu` (push and pop from both ends with O(1))
* `Counter` (makes counter dict of the iterrable)

#### Methods

* `sorted` - **O(n log n) worst, O(n) best**
