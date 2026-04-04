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




 

