# Priority Queue

* **Max Priority Queue**: the list will be arranged in descending order of their priority
* **Min Priority Queue**: the list will be arranged in ascending order of their priority

Three ways to implement Priority queue: \[[ref](https://pythonguides.com/priority-queue-in-python/)]

1. List
2. `queue.PriorityQueue`

```python
from queue import priorityQueue

pq = PriorityQueue()
pq.put((10,'Red balls'))
pq.put((8,'Pink balls'))
pq.put((5,'White balls'))
pq.put((4,'Green balls'))
while not pq.empty():
    item = pq.get() # POPS + return smallest priority item
    print(item)
    
# ” item “ then the output will appear as: 
# (4, ‘Green balls’) 
# (5, ‘White balls’) 
# (8, ‘Pink balls’) 
# (10, ‘Red balls’) ”
```

More priortyQueue functions:

* **qsize() –** Returns the current queue size.
* **empty() –** Returns True if the queue is empty, False otherwise. It is equivalent to qsize()==0.
* **full() –** Returns True if the queue is full, False otherwise. It is equivalent to qsize()>=maxsize.

3\. `heapq`&#x20;

```python
import heapq
pq = []
heapq.heappush(pq,(4, "Tom"))
heapq.heappush(pq,(1, "Aruhi"))
heapq.heappush(pq,(3, "Dyson"))
heapq.heappush(pq,(2, "Bob"))
while pq:
    deque_item = heapq.heappop(pq)
    print(deque_item)
    
#  (1, ‘Aruhi’) 
#  (2, ‘Bob’) 
#  (3, ‘Dyson’) 
#  (4, ‘Tom’)
```

### Resources

Theory:

* Wiliam [https://www.youtube.com/watch?v=wptevk0bshY\&list=PLDV1Zeh2NRsCLFSHm1nYb9daYf60lCcag\&index=2\&t=67s](https://www.youtube.com/watch?v=wptevk0bshY\&list=PLDV1Zeh2NRsCLFSHm1nYb9daYf60lCcag\&index=2\&t=67s)
* Abdul Bari [https://www.youtube.com/watch?v=HqPJF2L5h9U\&list=PLDN4rrl48XKpZkf03iYFl-O29szjTrs\_O\&index=33](https://www.youtube.com/watch?v=HqPJF2L5h9U\&list=PLDN4rrl48XKpZkf03iYFl-O29szjTrs\_O\&index=33)

Implementation:

* Three ways to implement prioirty queue in python: [https://pythonguides.com/priority-queue-in-python/](https://pythonguides.com/priority-queue-in-python/)

