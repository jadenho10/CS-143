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
    res = set(xs)
    remaining = fds
    changed = True

    while changed:
        changed = False
        next_remaining = []
        for (x, y) in remaining:
            if x.issubset(res):
                newAttr = y - res
                if newAttr:
                    res |= newAttr
                    changed = True
            else:
                next_remaining.append((x, y))
        remaining = next_remaining
    return res
```
The time complexity should be $O(n^2 \times m)$ with m FDs and n times. 

We can discard an FD as soon as it successfully applies because the closure grows monotonically. In other words, it's safe to remove it because we don't gain anything from keeping it in our sets of FDs. 


4. Check algorithm:
I'm gonna assume fds is a set of tuples where
x -> y := (x, y)

```python
def check(fds, fd):
"""Check if fd follows from fds"""
    x, y = fd
    return y.issubset(closure(fds, x)) 
```
5. Run the check algorithm to prove Angstrom's axioms.

Proof for $Y \subseteq X \implies X \rightarrow Y$.

check([], (X, Y)) => closure ([], X) = X

Since we have  $Y \subset X$, $X \rightarrow Y$

$\{ X \to Y \} \vdash X \cup Z \to Y \cup Z$

$(\{ X \to Y,\; Y \to Z \} \vdash X \to Z)$ 

6. Write a function to check if a given set of attributes $X$ is a superkey. 

If $X \rightarrow \Sigma$ where $\Sigma$ is the set of all table attributes

Function takes 3 args: X, Phi, Sigma

```python
def superkey(X, phi, sigma) -> bool:
    """
    Phi - all FDs that hold over table
    """
    return closure(fds, X) == sigma

```
7. Prove this algorithm correctly decomposes the table. 
```
def decompose(R):
  S = attributes of R
  find X s.t. X+ != X & X+ != S
  if not found:
    return
  else:
    break R into X+, R2(S - (X+ - X))
    decompose(R1) 
    decompose(R2)
```

8. Implement the algorithm in Python

9. 


