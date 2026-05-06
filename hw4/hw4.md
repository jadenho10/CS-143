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
    
    res += arr2[j:] + arr2[j:]
    return res

```

2. Merge Sort
```python
def mergesort(array):
    
    mergedList = []
    while len(array) > 1:

```