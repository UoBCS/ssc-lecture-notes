# Lecture 5 - 06/10/2015

## Query Language (QL) [ctd]

### Joined tables

A joined table is a table derived from two other tables according to the rules of the particular join type:

- inner
- outer
- cross-joins

For a visual explanation of the different joins follow this links:

1. [A visual explanation of SQL joins](http://blog.codinghorror.com/a-visual-explanation-of-sql-joins/).
2. [Visual representation of SQL joins](http://www.codeproject.com/Articles/33052/Visual-Representation-of-SQL-Joins)

The general syntax of a joined table is:

```sql
T1 join_type T2 [join_condition]
```

If more than one table reference is listed in the FROM clause, the tables are cross-joined (that is, the Cartesian product of their rows is formed):

```sql
SELECT *
FROM Students, Marks
WHERE Students.sid = Marks.sid
```

The last condition is called the **join condition**.

The type of join we performed can be performed using **INNER JOIN**

```sql
SELECT *
FROM Students S
INNER JOIN Marks M
ON S.sid = M.sid
```

### Correlation names

### UNION, INTERSECT, EXCEPT

### Nested queries

### GROUP BY and HAVING

### Views
