# Lecture 4 - 06/10/2015

## Data Manipulation Language (DML)

This subset of SQL allows users to pose queries and to insert, delete, and modify rows.

### INSERT statement

To insert rows into a table:

```sql
INSERT INTO Table VALUES (...)
```

or we can specify the columns:

```sql
INSERT INTO Table (...) VALUES (...)
```

Example:

```sql
INSERT INTO Students (sid, firstname, lastname, age) VALUES (103, John, Smith, 19)
```

It's possible to insert multiple rows in a single command:

```sql
INSERT INTO
Students (sid, firstname, lastname, age) VALUES
(103, John, Smith, 19),
(173, Clara, White, 20),
(186, Maria, Ed, 23);
```

### UPDATE statement

You can update individual rows, all the rows in a table, or a subset of all rows:

```sql
UPDATE Table SET columnname1 = columnvalue1 [WHERE columnname2 = columnvalue2]
```

Examples:

```sql
UPDATE Students SET age = 20 WHERE sid = 103;
```

```sql
UPDATE Students SET age = age + 1 WHERE sid = 186;
```

### DELETE statement

You can delete individual rows, all the rows in the table, or a subset of all rows:

```sql
DELETE FROM Table [WHERE columnname = columnvalue]
```

## Query Language (QL)

In SQL the SELECT command is used to specify queries. The general syntax of the SELECT command is:

```sql
SELECT column_list FROM table_expression [sort_specification]
```

### Examples

Simple query to retrieve an entire table:

```sql
SELECT * FROM Students;
```

We can also use expressions in the column list:

```sql
SELECT (a, b + c) from Table;
```

In general, table expressions can be complex constructs of base tables, joins, and subqueries

The table expression contains a FROM clause that is optionally followed by WHERE , GROUP BY , and HAVING clauses.

### DISTINCT clause

The DISTINCT clause remove duplicates from a result table:

```sql
SELECT DISTINCT course FROM Students
```

### Aggregate functions

Aggregate functions are used to compute against a returned column of numeric data from your SELECT statement.

Examples:

```sql
SELECT COUNT (DISTINCT course) AS NoC FROM Students;

SELECT AVG (salary) FROM Employees;

SELECT MAX (mark) FROM Marks WHERE sid = 123;
```

### WHERE clause

The syntax of the WHERE clause is:

```sql
WHERE search_condition 
```

After the processing of the FROM clause is done, each row of the derived virtual table is checked against the search condition.

Examples:

```sql
SELECT * FROM Test WHERE a > 5

SELECT * FROM Courses WHERE name IN ('CS', 'CSBM')

SELECT * FROM Marks WHERE cid IN (SELECT cid FROM Courses WHERE name IN ('CS', 'CSBM'))

SELECT * FROM Students WHERE age BETWEEN 18 AND 35

SELECT * FROM Students WHERE email IS NOT NULL
```

### LIKE

LIKE provides pattern matching on strings:

- `_` matches any character
- `%` matches 0 or more characters

Example:

```sql
SELECT * FROM Students WHERE name LIKE '_ob%'
```

### ORDER BY

Since we are dealing with sets (which by nature are unordered) if we wanted to have an ordering we must specify it as follows:

```sql
SELECT sid, firstname, lastname FROM Students ORDER BY lastname, firstname
```

When more than one expression is specified, the later values are used to sort rows that are equal according to the earlier values.

In our example if two (or more) last names are equal then we sort on the first name.


### LIMIT and OFFSET

LIMIT and OFFSET are used to retrieve just a portion of the rows that are generated by the rest of the query.

If both OFFSET and LIMIT appear, then OFFSET rows are skipped before starting to count the LIMIT rows that are returned.

Example:

```sql
SELECT * FROM Students LIMIT 2000 OFFSET 100
```

This will retrieve 2000 rows starting from the 100th row.

## References

1. Lecture notes
2. The PostgreSQL Global Development Group. (2001), PostgreSQL 9.4.4 Documentation.






