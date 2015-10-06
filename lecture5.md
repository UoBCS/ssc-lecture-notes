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

When disambiguities occur we should give different names to our tables:

```sql
SELECT S1.id, S2.id, S1.dob
FROM Student S1, Student S2
WHERE S1.dob = S2.dob AND S1.id > S2.id
```

### UNION, INTERSECT, EXCEPT

The results of two queries can be combined using the set operations union, intersection, and difference:

```sql
query1 UNION query2
query1 INTERSECT query2
query1 EXCEPT query2
```

Example (see lecture notes).

### Nested queries

It is possible to have subqueries whose results are then used in the outer query.

Subqueries are mainly used with these operators:

- [NOT] IN
- [NOT] EXISTS
- <op> ANY
- <op> ALL

### GROUP BY and HAVING

After passing the WHERE filter, the derived input table might be subject to grouping, using the GROUP BY clause, and filtering of group rows using the HAVING clause.

Examples:

```sql
SELECT customerName, SUM(orderQt)
FROM Sales
GROUP BY customerName
```

```sql
SELECT customerName, SUM(orderQt)
FROM Sales
GROUP BY customerName
HAVING SUM(orderQt) > 5
```

## References

1. Lecture notes
2. The PostgreSQL Global Development Group. (2001), PostgreSQL 9.4.4 Documentation.
