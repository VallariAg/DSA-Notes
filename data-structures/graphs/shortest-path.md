# Shortest Path

Shorted Path Algorithms:

### [Bellman Ford](https://www.programiz.com/dsa/bellman-ford-algorithm)

**Time**: `O(VE)` **Space**: `O(N)`

Bellman Ford algorithm helps us find **the shortest path from a vertex to all other vertices** of a weighted graph.

```python
def networkDelayTime(self, times: List[List[int]], N: int, K: int) -> int:
        dist = [float("inf") for _ in range(N)]
        dist[K-1] = 0
        for _ in range(N-1):
            for u, v, w in times:
                if dist[u-1] + w < dist[v-1]:
                    dist[v-1] = dist[u-1] + w
        return dist
```

### [Dijkstra](https://www.programiz.com/dsa/dijkstra-algorithm)

**Time:** `O(E+VlogV)` **Space:** `O(V+E)`

Dijkstra's algorithm allows us to find **the** **shortest path between any two vertices of a graph**.

Implementation can be done in naive way and easy way (with heaps - given below) \[[read here](https://pythonalgos.com/dijkstras-algorithm-in-5-steps-with-python/)]

```python
 def dijkstra(self, times: List[List[int]], root, destination) -> int:
       pyth weight = collections.defaultdict(dict)
        for u, v, w in times:
            weight[u][v] = w
        heap = [(0, root)]
        dist = {}
        while heap:
            time, u = heapq.heappop(heap)
            if u not in dist:
                dist[u] = time
                for v in weight[u]:
                    heapq.heappush(heap, (dist[u] + weight[u][v], v))
        return dist[destination]
```

### [Floyd Warshall](https://www.programiz.com/dsa/floyd-warshall-algorithm)

**Time**: `O(V^3)` **Space**: `O(V^2)`

Floyd-Warshall Algorithm is an algorithm for finding **the shortest path between all the pairs of vertices** in a weighted graph. This algorithm works for both the directed and undirected weighted graphs. But, it does not work for the graphs with negative cycles (where the sum of the edges in a cycle is negative).

```python
    def networkDelayTime(self, times: List[List[int]], N: int, K: int) -> int:
        dist = [[float("inf") for _ in range(N)] for _ in range(N)]
        for u, v, w in times:
            dist[u-1][v-1] = w
        for i in range(N):
            dist[i][i] = 0
        for k in range(N):
            for i in range(N):
                for j in range(N):
                    dist[i][j] = min(dist[i][j], dist[i][k]+dist[k][j])
                    
```

### [Shortest Path Faster Algorithm](https://www.geeksforgeeks.org/shortest-path-faster-algorithm/)

**Time:** average `O(E)`, worst `O(VE)` **Space:** `O(V+E)`

```python
    def networkDelayTime(self, times: List[List[int]], N: int, K: int) -> int:
        dist = [float("inf") for _ in range(N)]
        K -= 1
        dist[K] = 0
        weight = collections.defaultdict(dict)
        for u, v, w in times:
            weight[u-1][v-1] = w
        queue = collections.deque([K])
        while queue:
            u = queue.popleft()
            for v in weight[u]:
                if dist[u] + weight[u][v] < dist[v]:
                    dist[v] = dist[u] + weight[u][v]
                    queue.append(v)
                    
```

### Johnson



### Resources

* Understand algorithms from Programiz (click on algo heading above)
* Easy to Understand Path Algorithms with a basic question: [https://leetcode.com/problems/network-delay-time/discuss/283711/Python-Bellman-Ford-SPFA-Dijkstra-Floyd-clean-and-easy-to-understand](https://leetcode.com/problems/network-delay-time/discuss/283711/Python-Bellman-Ford-SPFA-Dijkstra-Floyd-clean-and-easy-to-understand)
