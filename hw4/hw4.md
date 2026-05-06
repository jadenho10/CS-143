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