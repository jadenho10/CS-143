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

select distinct a.x as i, b.x as j
from action a, action b
where a.t <= b.t
    and a.tx != b.tx
    and a.item = b.item
    and (a.op_i == "W" or b.op_j == "W"); 
```

3. Run the serializable function on the table:

4. Give a serializable, but not serial schedule

| T1 | T2 |
| -------- | -------- |
| R(A)   |    |
|   | R(B)   |
| W(A)   |     |
|    | W(B)   |

In this table, every read and write happens atomically.
This is serializable since T1 only touches item A and T2 only touches item B. Since we have B in between Read and Write of A, then this cannot be serial. 

5. Difference between 2PL and strict 2PL

In 2PL, locks are allowed to be released before the shrinking phase. However, this causes issues with dirty data. In strict 2PL, you must hold all of the locks until every transaction has made a commit or abort. 

6. 2-tx schedule with locks that is serializable but can't follow 2PL. 
