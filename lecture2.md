# Lecture 2 - 29/09/2015


## What is a DBMS?

A DBMS is a collection of tools that allows to store and manipulate data:
- Core data base -> representation of data, retrieval and mantainance of it
- Useful tools -> design, build and maintenance

## DB models

There are different DB models available for different data layouts:
- Network/Graph model
- Hierachical model
- Relational model (general purpose, commercial/enterprise systems)

## Properties

Databases are an **organised** collection of data so that it can be accessed and maintained efficiently and to facilitate some common operations.

Optimal databases have the following properties:
- Data independence from internal or physical representation
- Minimise redundancy
- Maximise consistency
- Integration and sharing
- Facitilitate change (refactoring)

## ACID

Necessary properties for a database are:

- **A**tomicity
- **C**onsistency
- **I**solation
- **D**urability

## ANSI/SPARC DB architecture

This architecture separates database functionalities into:
- **Physical** or internal data model
- **Conceptual** data model
- **View** or external data model

## DB models' languages

All the above DB models include a **data definition language (DDL)** for specifying the structural aspects of the data, a **data manipulation language (DML)**
for accessing and updating it and a **query language (QL)**.
