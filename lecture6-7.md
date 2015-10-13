# Lectures 5 & 6 - 12-13/10/2015

## What is JDBC?

JDBC provides a mechanism for connection to database systems using Java. The API provides:

- Managing multiple connections
- Sending queries to the DB
- Receiving results from the DB
- Updating the DB tables (DDL)

## Workflow

- Make connection
- Issue request
- Process result 
- Close connection

## Development notes

For development and debugging purposes it is good practice to separate the code that creates, populate and destroys the database from
the actual application.

## Preparing the environment

Download the appropriate driver/connector from the vendor website (e.g. [https://jdbc.postgresql.org/download.html](https://jdbc.postgresql.org/download.html))

Using Eclipse:

- Right click on your projects folder
- Build Path > Add external archive
- Include the downloaded JAR

The packages to import are:

- `java.sql.*`
- `javax.sql.*`

### Example

```java

try {
	Class.forName("org.postgresql.Driver");
}
catch (ClassNotFoundException e) {
	System.out.println("Driver not found");
}

System.out.println("PostgreSQL driver registered.");

Connection = null;
String url = "jdbc:postgresql://<server>/<database>"

try {
	conn = DriverManager.getConnection(url, username, pass);
} catch (SQLException ex) {
	ex.printStackTrace();
}

if (conn != null) {
	// Do your work!
}
else {
	// Failed to make connection
}

```

## Statements

### Statement object

### PreparedStatement object

## 


## References

1. Lecture notes

