1. 
```python
def merge(arr1, arr2):
    res = []
    i, j = 0, 0
    while i < len(arr1) and j < len(arr2):
        if arr1[i] < arr2[j]:
            res.append(arr1[i])
            i += 1
        else:
            res.append(arr2[j])
            j += 1
    
    res += arr1[i:] + arr2[j:]
    return res

```

2. Merge Sort
```
1. Divide the array into halves. Stop when you have arrays of size 1. 
2. Res = []
3. Combine the arrays with the merge function. Do it until we have an array size == original array
```

3. 
```sql
SELECT x, SUM(y) FROM t GROUP BY x ORDER BY x ASC;
```

4. Implement the query SELECT * FROM r, s WHERE r.y = s.y using sort-merge join. The table r has columns x, y, and s has columns y, z. Make sure you handle duplicates correctly.

```sql
SELECT * FROM r, s WHERE r.y = s.y GROUP BY y
```

5. Implement the group by-aggregate query above using a map (dictionary) instead.

6. Implement the join query above using a map (dictionary) instead.
