# Circular Queue

**Complexity:**

Time: O(1) for every operation, apart from initialization.\
Memory: O(N) where N is the capacity of our queue.

**Code:**

```
class MyCircularQueue:

    def __init__(self, k: int):
        self.array = [0] * k
        self.rear = -1
        self.size = 0
        self.capacity = k

    def enQueue(self, value: int) -> bool:
        if self.isFull(): return False
        self.rear = (self.rear + 1) % self.capacity
        self.array[self.rear] = value
        self.size += 1
        return True

    def deQueue(self) -> bool:
        if self.isEmpty(): return False
        self.size -= 1
        return True

    def Front(self) -> int:
        if self.isEmpty(): return -1
        return self.array[(self.rear-self.size+1) % self.capacity]

    def Rear(self) -> int:
        if self.isEmpty(): return -1
        return self.array[self.rear]

    def isEmpty(self) -> bool:
        return not self.size

    def isFull(self) -> bool:
        return self.size == self.capacity

```

