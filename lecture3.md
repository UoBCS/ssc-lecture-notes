# Lecture 3 - 05/10/2015

## Some definitions

The main construct for representing data in the relational model is a **relation** which consists of a **relation schema** and a **relation instance**

- Relation instance: the table (a set of **tuples** or **rows**)
- Relation schema: specifies the relation's name, the name of each field, and the domain of each field.
- Cardinality: the number of tuples in a relation instance
- Arity: the number of fields in the relation schema

## Data Definition Language

### CREATE TABLE

The **CREATE TABLE** statement is used to define a new table:

```sql
CREATE TABLE Students (
	
	sid INTEGER,
	name CHAR(30),
	login CHAR(20),
	age INTEGER
	
);
```

In general:

```sql
CREATE TABLE [table name] ( [column definitions] ) [table parameters]
```

### DROP TABLE

The **DROP TABLE** statement is used to delete a table:

```sql
DROP TABLE Students [RESTRICT|CASCADE];
```

### ALTER TABLE

The **ALTER TABLE** statement is used to modify an existing table:

```sql
ALTER TABLE Students ADD dob DATE;
ALTER TABLE Students DROP COLUMNS dob;
ALTER TABLE Courses DROP CONSTRAINT fk_CoursesStudents
```

## SQL Types

Check this [web page](http://www.w3schools.com/sql/sql_datatypes_general.asp).

## Domain constraints

We can also enforce additional constraints over values.

In SQL we have the following domain constraints:

- NOT NULL
- UNIQUE
- CHECK
- DEFAULT

Example of `CHECK`

```sql
CREATE TABLE Students (
	
	sid INTEGER,
	name CHAR(30),
	login CHAR(20),
	age INTEGER
	CHECK (age >= 18)
	
);
```

## Integrity Constraints over relations

An **integrity constraint** is a condition that is specified on a database schema, and restricts the data that can be
stored in an instance of the database.

A DBMS **enforces** integrity constraints, in that it permits only legal instances to be stored in the database.

### Key Constraints

In SQL we can declare that a subset of the columns of a table constitute a key by
using the **UNIQUE** constraint. At most one of these candidate keys can be declared
to be a primary key, using the PRIMARY KEY constraint.

Key constraints signal importance to DB structure rather than just a data/domain constraint.

#### Primary keys

First way:

```sql
CREATE TABLE Students (
	sid INTEGER,
	name CHAR(30),
	login CHAR(20),
	age INTEGER,
	CONSTRAINT StudentsKey PRIMARY KEY (sid)
)
```

Second way:

```sql
CREATE TABLE Students (
	sid INTEGER,
	name CHAR(30),
	login CHAR(20),
	age INTEGER,
	PRIMARY KEY (sid)
)
```

Third way:

```sql
CREATE TABLE Students (
	sid INTEGER PRIMARY KEY,
	name CHAR(30),
	login CHAR(20),
	age INTEGER
)
```

#### Foreign keys

Foreign keys are used to link relations to each other.

```sql
CREATE TABLE Courses (
	cid INTEGER PRIMARY KEY,
	name CHAR(20),
	sid INTEGER,
	FOREIGN KEY (sid) REFERENCES Students(sid)
)
```

### Enforcing integrity constraints

What shoud we do when we delete a student tuple? What should happen to the referenced rows in the Courses table?

The options are:

- Delete all rows that refer to the deleted row.
- Disallow the deletion of the Students row if a Courses row refers to it.
- For every Course row that refers to it, set the sid column to null

What should we do if the primary key value of a Students row is updated?

The options are the same as above.

The general sytax is: ON [DELETE|UPDATE] [NO ACTION|RESTRICT|CASCADE|SET NULL]

Example:

```sql
CREATE TABLE Courses (
	cid INTEGER PRIMARY KEY,
	name CHAR(20),
	sid INTEGER,
	FOREIGN KEY (sid) REFERENCES Students(sid)
		ON DELETE CASCADE
		ON UPDATE NO ACTION
) 
```

## References

1. Lecture notes
2. RAMAKRISHNAN, R. and GEHRKE, J. (2002) Database Management Systems. 2nd Edition
3. W3SCHOOLS. SQL Constraints. [Online] Available from: http://www.w3schools.com/sql/sql_constraints.asp. [Accessed: 05th October 2015].

