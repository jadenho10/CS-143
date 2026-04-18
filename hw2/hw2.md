1. Creating a set in Python:
use the set() built-in class. 

2. Algorithm is simple:
```python
def union(set1, set2):
    union = {}
    for elem in set1:
        if elem in set2: union.add(elem)
    return union

```

3. Closure algorithm in Python:
```python
def closure(fds, xs):
  """Compute the closure of xs over fds

  Arguments:
  fds: the set of input fds
  xs: the set of attributes to take closure of
  """
    c = xs
    while True:
        before = c.copy() # this is to check later if the set changes or not
        for x, y in fds:
            if x in c:
                c.add(y)
        if c == before:
            break
    return c
```
The time complexity should be $O(n^2 \times m)$

4. Check algorithm:
I'm gonna assume fds is a set of tuples where
x -> y := (x, y)

This can be a graph problem tbh. Use BFS
```python
def check(fds, fd):
"""Check if fd follows from fds"""
    lhs, rhs = fd  # retrieving both attributes e.g. x -> y  lhs = x, rhs = y
    adjList = defaultdict(list)
    for left, right in fds:
        adjList[left].append(right)
    
    q = deque([lhs])
    visit = set()
    visit.add(lhs)
    while q:
        node = q.popleft()
        if node == rhs:
            return True
        for nei in adjList[node]:
            if nei not in visit:
                q.append(nei)
                visit.add(nei)
    return False
```
5. Run the check algorithm to prove Angstrom's axioms.

Proof for $Y \subseteq X \implies X \rightarrow Y$.

 
