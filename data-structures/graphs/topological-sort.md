# Topological Sort

* sort so every directed edge u-v, vertex **u** comes before **v** in the ordering.
* It has no 1 solution (many acceptable sorted arrays)
* Only possible for DAG (directed acyclic graph)
* Used to detect cycles in graph
* Time complexity: `O(E+V)`



Implementation:

1. Make adj list
2. Loop through all nodes and do DFS on each
3. In DFS, maintain local "visiting" set which tracks for cycles.

```python
class Solution:
    def findOrder(self, numCourses: int, prerequisites: List[List[int]]) -> List[int]:
        adj_list = collections.defaultdict(list)
        for curr, preq in prerequisites:
            adj_list[curr] += [preq]
        ans = []
        in_ans = set()


        def dfs(curr, visiting):
            nonlocal ans
            nonlocal in_ans
            if curr in in_ans:
                return True
            if curr in visiting:
                return False
            visiting.add(curr)
            for i in adj_list[curr]:
                if not dfs(i, visiting):
                    return False
            visiting.remove(curr)
            ans += [curr]
            in_ans.add(curr)
            return True
        
        for i in range(numCourses):
            if not dfs(i, set()):
                return []
        return ans

```



* Question that teaches topological sort: [https://leetcode.com/problems/course-schedule-ii/description/](https://leetcode.com/problems/course-schedule-ii/description/)
* How to solve above question: [https://www.youtube.com/watch?v=Akt3glAwyfY](https://www.youtube.com/watch?v=Akt3glAwyfY)
