# Shortest Path

Shorted Path Algorithms:



### [Bellman Ford](https://www.programiz.com/dsa/bellman-ford-algorithm)





### [Dijkstra](https://www.programiz.com/dsa/dijkstra-algorithm)

Implementation can be done in naive way and easy way (with heaps - given below) \[[read here](https://pythonalgos.com/dijkstras-algorithm-in-5-steps-with-python/)]

```python
 def dijkstra(self, times: List[List[int]], root) -> int:
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
```



### [Floyd Warshall](https://www.programiz.com/dsa/floyd-warshall-algorithm)

###

### Johnson



### Resources

* Understand algorithms from Programiz (click on algo heading above)
* Easy to Understand Path Algorithms with a basic question: [https://leetcode.com/problems/network-delay-time/discuss/283711/Python-Bellman-Ford-SPFA-Dijkstra-Floyd-clean-and-easy-to-understand](https://leetcode.com/problems/network-delay-time/discuss/283711/Python-Bellman-Ford-SPFA-Dijkstra-Floyd-clean-and-easy-to-understand)
