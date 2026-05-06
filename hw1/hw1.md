# HW 1

1. You can call "sqlite3 --version"
2. CREATE tablename, INSERT INTO table (val1, val2) VALUES (val1, val2)
3. run table
```bash
jaden@MacBook-Pro-3 CS-143 % sqlite3 hw1.sqlite
SQLite version 3.51.0 2025-06-12 13:14:41
Enter ".help" for usage hints.
sqlite> 
sqlite> CREATE TABLE Students (
(x1...>     name  TEXT NOT NULL,
(x1...>     UID   BIGINT,
(x1...>     major TEXT
(x1...> );
sqlite> 
sqlite> INSERT INTO Students (name, UID, major)
   ...> VALUES 
   ...>     ('John Doe',     100200300,  'Computer Science'),
   ...>     ('Emily Watson', 911402452,  'Biology'),
   ...>     ('Peer Luck',    3591250698, 'Gender Studies');
sqlite> 
```
4. 
```sql
SELECT * FROM R WHERE R.x < 3
```
"SELECT *" retreives all columns from a table. 

```sql
CREATE TABLE R (
    x bigint,
  	y bigint,
  	PointName text
);

INSERT INTO R (x, y, PointName)
VALUES (3, 4, 'Black'), 
(2, 5, 'Yellow'), 
(1, 1, 'Green'), 
(10, 5, 'Red');    
```

```sql
CREATE TABLE R (
    x bigint,
    y bigint,
    PointName text
);

INSERT INTO R (x, y, PointName)
VALUES (1, 4, 'Black'), 
(2, 5, 'Yellow'), 
(1, 1, 'Green'), 
(1, 5, 'Red');

SELECT * FROM R WHERE R.x < 3 
```

The output will exclude the (10, 5, Red) row which will be fewer rows than R. 

Adding more rows from SELECT is impossible in this scenario. You can only discard or add the amount
of rows you have. 

5. SELECT x + x FROM R 
Same number of rows:
```sql
CREATE TABLE R (
    x bigint,
    y bigint,
    PointName text
);

INSERT INTO R (x, y, PointName)
VALUES (1, 4, 'Black'), 
(2, 5, 'Yellow'), 
(1, 1, 'Green'), 
(1, 5, 'Red');

SELECT x + x FROM R 
```

Fewer rows and More rows is impossible! The query always outputs the same number of rows 
requested by the table. 


6. SELECT DISTINCT x FROM R
This has to return all UNIQUE x from the table R. 
 
Having MORE rows in a distinct output is impossible. Len(set(X)) <= Len(X)

a) The query outputs fewer rows than SELECT x, avg(y) FROM R GROUP BY x


This will output only one row. 
```sql
CREATE TABLE R (
    x bigint,
    y bigint,
    PointName text
);

INSERT INTO R (x, y, PointName)
VALUES (1, 4, 'Black'), 
(1, 5, 'Yellow'), 
(1, 1, 'Green'), 
(1, 5, 'Red');
```


This will output every row.
```sql
CREATE TABLE R (
    x bigint,
    y bigint,
    PointName text
);

INSERT INTO R (x, y, PointName)
VALUES (1, 4, 'Black'), 
(2, 5, 'Yellow'), 
(3, 1, 'Green'), 
(4, 5, 'Red');
```

Outputting more rows is impossible. The number of rows is limited by the unique number of x elems
which is the amount of rows in the og table. 

7. SELECT * FROM R, S WHERE R.x = S.y where j is the output size.

$j \leq r + s$ 

$j \leq r * s$ 

$j \geq \min(r, s)$ 

$j \geq \max(r, s)$ 

Make some tables that violate these conditions

This cannot violate r * s but can for r + s.

JOIN can have at most R x S.

8. Pointwise Product

```sql
SELECT a_v * b_v AS values FROM a, b WHERE a_i = b_i;
```

9. Dot Product

```sql
SELECT SUM(a_v * b_v) AS dot_product FROM a, b WHERE a_i = b_i;
```
10. Outer Product
We want to multiply every value in a & b so we can use CROSS JOIN. 

```sql
SELECT a_i, b_i AS j, a_v * b_v AS v 
FROM a, b 
```
11. Matrix Product
$C_{ik} = \sum_j A_{ij}B_{jk}$ 

Assuming that we have two tables A, B with columns i, j, v: 

```sql
SELECT a.i, b.j AS k, sum(a.v * b.v) AS v
FROM a, b
WHERE a.j = b.i
ORDER BY a.i, b.j
```

12. 
No changes needed. The inner JOIN naturally will skip over any missing entries, which is fine. You only need to compute entries nonzero. 

If you're multiplying something by zero, you get zero regardless of the number (mathematicians could debate this for other random things like infinity, not my problem). 

So sparse tables are closed under SQL tables. 

13. Semijoin:
```sql
SELECT * FROM R 
WHERE EXISTS (SELECT 1 FROM S WHERE R.y = S.y)
```

14. What are possible relationships between $|R \bowtie S|$ and $|R \ltimes S|$?

$|R \ltimes S| \leq |R \bowtie S|$.

15. 

16. What happens when SELECT evaluates to null?
SELECT will essentially return NULL with whatever value you have. 

You won't have an empty table.

17. 
Data operators, predicates, logical connectives with NULLS. 

You will sometimes get Unknown and sometimes get something else.

It's sometimes possible to not ended up with UNKNOWN even if an input data value is NULL?
```sql
SELECT * FROM r WHERE 2 != 2 AND NULL
```

18. 
We say a column k is a primary key of a table, if the value in that column uniquely identifies the row. Write a SQL query to check if a given column is a primary key. (hint: one way to do this is with GROUP BY and HAVING; another way is to use COUNT(DISTINCT ...). Make sure you know how to do it both ways.)

Method 1:
```sql
SELECT k 
FROM R 
GROUP BY x
HAVING COUNT(*) > 1
```
Method 2:
```sql
SELECT 1 HAVING COUNT(*) = COUNT(DISTINCT k)
```

19. Given a primary k in R, a column f in S is a foreign key referencing R.k if every 
value of S.f also appears in R.k. Write a SQL query to check if a given column S.f 
can be a foreign key referencing R.k. 

```sql
SELECT * FROM S WHERE EXISTS (SELECT 1 WHERE R.k = S.f) 
```

This returns all valid ones. 









 

