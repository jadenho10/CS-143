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

6. SELECT DISTINCT x FROM R
This has to return all UNIQUE x from the table. 

7. 

