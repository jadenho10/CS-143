1. Compute the algorithm to compute the precedence graph of a schedule. 

```python
def precedence(schedule):
    '''
    arguments: schedule (t, tx, op, item)
    return: set of edges meaning tx i must precede j
    '''
    edges = set()
    schedule.sort()
    for k, (t_i, i, op_i, x) in enumerate(schedule):
        for (t_j, j, opt_j, y) in schedule[:k + 1]:
            if t_i <= t_j and i != j and x == y 
                and (op_i == "W" or op_j == "W"):
                edges.add((i, j))
    return edges

```
2. SQL query 
```sql
create table action (
  t    int,   -- timestamp (ties allowed across tx)
  tx   int,   -- transaction id
  op   text,  -- 'R' or 'W'
  item text   -- DB item
);


```