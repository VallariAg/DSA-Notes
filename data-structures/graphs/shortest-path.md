# Shortest Path

Shorted Path Algorithms:

Negative cycles -> where the sum of the edges in a cycle is negative. It's not possible to find shortest path with negative cycles. Question would usually ask to "detect" it only. Only Bellman Ford can detect with negative cycles.

Let `u` be source node, `v` be destination node, `w` be weight of the edge between the `u` and `v`.

### [Bellman Ford](https://www.programiz.com/dsa/bellman-ford-algorithm)

**Time**: `O(VE)` **Space**: `O(N)`

Bellman Ford algorithm helps us find **the shortest path from a vertex to all other vertices** of a weighted graph.

* Uses edges as inputs `[[u, v, w]]`
* Slower than Dijkstra
* Able to use negative edges.
* Used to detected negative cycles. (If Nth iteration of loop determines negative-cycles)

<pre class="language-python"><code class="lang-python"><strong>def networkDelayTime(self, times: List[List[int]], N: int, K: int) -> int:
</strong>        dist = [float("inf") for _ in range(N)]
        dist[K-1] = 0
        for _ in range(N-1):
            for u, v, w in times:
                if dist[u-1] + w &#x3C; dist[v-1]:
                    dist[v-1] = dist[u-1] + w
        # nth loop determines negative cycles
        for u, v, w in times:
            if dist[u-1] + w &#x3C; dist[v-1]:
                return None # negative cycles detected!
        return dist
</code></pre>

### [Dijkstra](https://www.programiz.com/dsa/dijkstra-algorithm)

**Time:** `O(E logV)` **Space:** `O(V+E)`

Dijkstra's algorithm allows us to find **the** **shortest path between any two vertices of a graph**.

* Input has to be changed to `{u:{v: w}}`
* Only for non-negative edges.
* Don't work with negative cycles.
* Differs from the minimum spanning tree because the shortest distance between two vertices might not include all the vertices of the graph.

[https://www.youtube.com/watch?v=EaphyqKU4PQ](https://www.youtube.com/watch?v=EaphyqKU4PQ)

Implementation can be done in naive way and easy way (with min-heaps/pq - given below) \[[read here](https://pythonalgos.com/dijkstras-algorithm-in-5-steps-with-python/)]

<pre class="language-python"><code class="lang-python"> def dijkstra(self, times: List[List[int]], root, destination) -> int:
<strong>        weight = collections.defaultdict(dict)
</strong>        for u, v, w in times:
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
</code></pre>

### [Floyd Warshall](https://www.programiz.com/dsa/floyd-warshall-algorithm)

**Time**: `O(V^3)` **Space**: `O(V^2)`

Floyd-Warshall Algorithm is an algorithm for finding **the shortest path between all the pairs of vertices** in a weighted graph.&#x20;

* Works for both the directed and undirected weighted graphs.&#x20;
* Does not work for the graphs with negative cycles.
* Uses DP and 2D array to solve it.&#x20;

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
        return max(dist[K-1]) if max(dist[K-1]) < float("inf") else -1
                    
```

### [Shortest Path Faster Algorithm](https://www.geeksforgeeks.org/shortest-path-faster-algorithm/)

**Time:** average `O(E)`, worst `O(VE)` **Space:** `O(V+E)`

Based on Bellman Ford.

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



***

### Comparing&#x20;

* It is similar to Dijkstra's algorithm but it can work with graphs in which edges can have negative weights. Dijkstra's algorithm has better time complexity than BF.



### Resources

* Understand algorithms from Programiz (click on algo heading above)
* Easy to Understand Path Algorithms with a basic question: [https://leetcode.com/problems/network-delay-time/discuss/283711/Python-Bellman-Ford-SPFA-Dijkstra-Floyd-clean-and-easy-to-understand](https://leetcode.com/problems/network-delay-time/discuss/283711/Python-Bellman-Ford-SPFA-Dijkstra-Floyd-clean-and-easy-to-understand)
