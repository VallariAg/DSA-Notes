# DFS / BFS

DFS: [https://www.programiz.com/dsa/graph-dfs](https://www.programiz.com/dsa/graph-dfs)

```python
# DFS algorithm (uses stacks in iterative)
def dfs(graph, start, visited=None):
    if visited is None:
        visited = set()
    visited.add(start)

    print(start)

    for destination in graph[start] - visited:
        dfs(graph, destination, visited)
    return visited


graph = {'0': set(['1', '2']),
         '1': set(['0', '3', '4']),
         '2': set(['0']),
         '3': set(['1']),
         '4': set(['2', '3'])}

dfs(graph, '0')
```

BFS: [https://www.programiz.com/dsa/graph-bfs](https://www.programiz.com/dsa/graph-bfs)

```python
import collections

def bfs(graph, root):

    visited, queue = set(), collections.deque([root])
    visited.add(root)

    while queue:
        vertex = queue.popleft()
        print(str(vertex) + " ", end="")

        for neighbour in graph[vertex]:
            if neighbour not in visited:
                visited.add(neighbour)
                queue.append(neighbour)


graph = {0: [1, 2], 1: [2], 2: [3], 3: [1, 2]}
bfs(graph, 0)
```



