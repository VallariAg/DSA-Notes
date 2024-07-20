# Python Tricks

### Array

```python
array = [1, 1, 1, 3]

array.count(1) # 3
array.find(1) # 0 
array.rfind(1) # 2
array.find(2) # -1 
```

Dict

```python
d ={}
d.get('cat', 0) # 0 - setting default if key doesn't exist
```

```python
from collections import defaultdict

d = defaultdict(int) # (dict, but if key doesn't exist then create one with some default value)
d['cat'] # 0
```

Set

Tuple

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

### Libaries&#x20;

* `defaultdict` (dict, but if key doesn't exist then create one with some default value)
* `dequeu` (push and pop from both ends with O(1))
* `Counter` (makes counter dict of the iterrable)
