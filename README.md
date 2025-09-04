# JDBC (Java Database Connectivity) in Java

## Introduction

JDBC (Java Database Connectivity) is a powerful and essential technology that allows Java applications to interact with relational databases. It provides a standardized API (Application Programming Interface) for connecting to databases, executing SQL queries, and processing query results. JDBC is a part of the Java Standard Edition (Java SE) and is widely used in developing data-driven Java applications.

## What is JDBC (Java Database Connectivity)?

JDBC (Java Database Connectivity) is a Java API that provides a standard way to interact with databases. It allows Java applications to establish a connection to a database, send SQL queries to the database, and retrieve results from the queries. JDBC acts as a bridge between the Java application and the database, making it possible to create dynamic and data-driven Java applications.

## Types of Databases Present

JDBC supports various types of databases, including:

1. MySQL
2. Oracle Database
3. PostgreSQL
4. Microsoft SQL Server
5. SQLite
6. And many more...

## JDBC (Java Database Connectivity) Process

The JDBC process involves several steps:

1. Load the JDBC driver using `Class.forName()`.
2. Establish a connection to the database using `DriverManager.getConnection()`.
3. Create a statement or a prepared statement to execute SQL queries.
4. Execute the SQL queries using `Statement.execute()` or `PreparedStatement.execute()`.
5. Process the query results using `ResultSet`.

## JDBC Architecture in Java

JDBC follows a layered architecture consisting of:

1. **JDBC API:** The top layer that provides interfaces and classes for database connectivity and query execution.
2. **Driver Manager:** Manages the available JDBC drivers and selects the appropriate driver for database connectivity.
3. **JDBC Driver:** Acts as a bridge between the Java application and the database. There are four types of JDBC drivers:
   - Type 1 (JDBC-ODBC Bridge)
   - Type 2 (Native-API Partly Java Driver)
   - Type 3 (Network Protocol Pure Java Driver)
   - Type 4 (Thin Pure Java Driver)
4. **JDBC Database:** Represents the actual database where data is stored and retrieved.

## Types of JDBC Drivers in Java

JDBC drivers fall into four categories:

1. **Type 1 (JDBC-ODBC Bridge):** Uses the ODBC API to connect to the database. Requires ODBC drivers on the system.

2. **Type 2 (Native-API Partly Java Driver):** Converts JDBC calls into native database API calls. May require native libraries.

3. **Type 3 (Network Protocol Pure Java Driver):** Communicates with a middleware server acting as an intermediary between Java app and database.

4. **Type 4 (Thin Pure Java Driver):** Communicates directly with the database using a pure Java implementation. Most commonly used and recommended.

## 5 JDBC Stages in Java

1. **Load the JDBC Driver:** Load the appropriate JDBC driver using `Class.forName()`.

2. **Establish a Connection:** Use `DriverManager.getConnection()` to establish a connection to the database.

3. **Create a Statement or Prepared Statement:** Create either a `Statement` or `PreparedStatement` for executing SQL queries.

4. **Execute Queries:** Use `Statement.execute()` or `PreparedStatement.execute()` to execute SQL queries.

5. **Process Results:** Handle the query results using `ResultSet`.

## JDBC Components

In addition to the JDBC drivers, there are several other components that make up the JDBC API, including:

	** DriverManager Class **
	* Connection interface
	* Statement and PreparedStatement interfaces
	* ResultSet interface

These components work together to provide a powerful and flexible API for working with databases in Java.

## SQL Queries

SQL (Structured Query Language) is used to interact with databases. Common SQL queries include:

1. **Create SQL Query:** Used to create new database tables.

2. **Insert SQL Query:** Used to insert new records into a table.

3. **Update SQL Query:** Used to update existing records in a table.

4. **Delete SQL Query:** Used to delete records from a table.

5. **Read SQL Query:** Used to retrieve data from a table.

## Let's Start Creating Our Java MySQL CRUD Project in Eclipse

In this section, we'll create a simple Java application that performs CRUD (Create, Read, Update, Delete) operations on a MySQL database.

**Step 1:** Set up the MySQL database and create a table using SQL queries.

```sql
CREATE DATABASE mydatabase;
USE mydatabase;
CREATE TABLE users (
  id INT PRIMARY KEY AUTO_INCREMENT,
  name VARCHAR(50),
  age INT
);
```

**Step 2:** Create a new Java project in Eclipse and configure the MySQL JDBC driver.

**Step 3:** Implement the CRUD operations using JDBC in Java.

```java
// Import required packages
import java.sql.*;

public class JDBCDemo {
    // JDBC driver and database URL
    static final String JDBC_DRIVER = "com.mysql.cj.jdbc.Driver";
    static final String DB_URL = "jdbc:mysql://localhost/mydatabase";

    // Database credentials
    static final String USER = "your_username";
    static final String PASS = "your_password";

    public static void main(String[] args) {
        Connection conn = null;
        Statement stmt = null;

        try {
            // Register JDBC driver
            Class.forName(JDBC_DRIVER);

            // Open a connection
            System.out.println("Connecting to database...");
            conn = DriverManager.getConnection(DB_URL, USER, PASS);

            // Create a statement
            stmt = conn.createStatement();

            // Perform CRUD operations
            // ... (Implement create, read, update, delete operations)

            // Clean-up environment
            stmt.close();
            conn.close();
        } catch (SQLException se) {
            se.printStackTrace();
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            // Close resources
            try {
                if (stmt != null) stmt.close();
            } catch (SQLException se) {
                se.printStackTrace();
            }
            try {
                if (conn != null) conn.close();
            } catch (SQLException se) {
                se.printStackTrace();
            }
        }
        System.out.println("Goodbye!");
    }
}
```

**Step 4:** Run the Java application and verify the CRUD operations in the MySQL database.

## Let's Understand the JDBC Code

The JDBC code can be broken down into the following sections:

1. **Register JDBC Driver:** Use `Class.forName(JDBC_DRIVER)` to load and register the JDBC driver.

2. **Open a Connection:** Use `DriverManager.getConnection(DB_URL, USER, PASS)` to establish a connection to the database.

3. **Create a Statement:** Use `Connection.createStatement()` to create a statement for executing SQL queries.

4. **Perform CRUD Operations:** Implement the CRUD operations using SQL queries and `Statement.execute()`.

5. **Clean-up Environment:** Close the statement and connection in the `finally` block to release resources.

## Let's Try to Load the JDBC Driver

While executing the JDBC code, you may encounter issues related to loading the JDBC driver. To resolve this, make sure you have added the JDBC connector jar file to your project's classpath.

## Why JDBC Driver Is Not Loading?

If the JDBC driver is not loading, it may be due to:

1. Incorrect JDBC driver class name in `JDBC_DRIVER`.
2. Missing JDBC connector jar file in the project's classpath.

## Adding JDBC Connector Jar File in Project

To add the JDBC connector jar file to your project, follow these steps:

1. Download the appropriate JDBC connector jar file for your DBMS.
2. In Eclipse, right-click on the project and select "Build Path" > "Configure Build Path."
3. In the "Libraries" tab, click "Add External JARs" and select the downloaded JDBC connector jar file.

## How to Verify JDBC Connection Is Successful or Not?

To verify the JDBC connection, you can add a simple check after establishing the connection:

```java
if (conn != null) {
    System.out.println("Database connected successfully!");
} else {
    System.out.println("Failed to connect to the database.");
}
```

## Important Point to Remember

When working with JDBC, always remember to close the `Connection`, `Statement`, and `ResultSet` objects after using them to free up resources and avoid potential memory leaks.

## Let's Create a New JDBC Setup Class

To better organize the JDBC code, let's create a separate class to handle the JDBC setup:

```java
public class JdbcSetup {
    // JDBC driver and database URL
    static final String JDBC_DRIVER = "com.mysql.cj.jdbc.Driver";
    static final String DB_URL = "jdbc:mysql://localhost/mydatabase";

    // Database credentials
    static final String USER = "your_username";
    static final String PASS = "your_password";

    // Connection object
    private Connection conn;

    // Constructor to initialize the connection
    public JdbcSetup() {
        try {
            // Register JDBC driver
            Class.forName(JDBC_DRIVER);

            // Open a connection
            System.out.println("Connecting to database...");
            conn = DriverManager.getConnection(DB_URL, USER, PASS);
        } catch (SQLException se) {
            se.printStackTrace();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    // Getter method to access the connection
    public Connection getConnection() {
        return conn;
    }

    // Close the connection
    public void closeConnection() {
        try {
            if (conn != null) conn.close();
        } catch (SQLException se) {
            se.printStackTrace();
        }
    }
}
```

## Create Table Operation Using JDBC in Java

To create a table in the database using JDBC, use the `Statement.execute()` method with a create SQL query:

```java
JdbcSetup jdbcSetup = new JdbcSetup();
Connection conn = jdbcSetup.getConnection();

Statement stmt = conn.createStatement();
String createTableSQL = "CREATE TABLE IF NOT EXISTS users (id INT PRIMARY KEY AUTO_INCREMENT, name VARCHAR(50), age INT)";
stmt.execute(createTableSQL);

stmt.close();
jdbcSetup.closeConnection();
```

## CRUD Operations in JDBC

CRUD stands for Create, Read, Update, and Delete, which are the basic operations performed on database records.

### Create Data Operation Using JDBC in Java

To insert data into the database using JDBC, use the `Statement.execute()` method with an insert SQL query:

```java
JdbcSetup jdbcSetup = new JdbcSetup();
Connection conn = jdbcSetup.getConnection();

Statement stmt = conn.createStatement();
String insertDataSQL = "INSERT INTO users (name, age) VALUES ('John', 30)";
stmt.execute(insertDataSQL);

stmt.close();
jdbcSetup.closeConnection();
```

### Read Data Operation Using JDBC in Java

To read data from the database using JDBC, use the `Statement.executeQuery()` method with a select SQL query:

```java
JdbcSetup jdbcSetup = new JdbcSetup();
Connection conn = jdbcSetup.getConnection();

Statement stmt = conn.createStatement();
String readDataSQL = "SELECT * FROM users";
ResultSet resultSet = stmt.executeQuery(readDataSQL);

while (resultSet.next()) {
    int id = resultSet.getInt("id");
    String name = resultSet.getString("name");
    int age = resultSet.getInt("age");
    System.out.println("ID: " + id + ", Name: " + name + ", Age: " + age);
}

resultSet.close();
stmt.close();
jdbcSetup.closeConnection();
```

### Update Data Operation Using JDBC in Java

To update data in the database using JDBC, use the `Statement.execute()` method with an update SQL query:

```java
JdbcSetup jdbcSetup = new JdbcSetup();
Connection conn = jdbcSetup.getConnection();

Statement stmt = conn.createStatement();
String updateDataSQL = "UPDATE users SET age = 35 WHERE name = 'John'";
stmt.execute(updateDataSQL);

stmt.close();
jdbcSetup.closeConnection();
```

### Difference Between Execute, ExecuteUpdate & ExecuteQuery

- `execute()`: Used for DDL (Data Definition Language) statements like CREATE, ALTER, and DROP. Returns `true` if the first result is a ResultSet, `false` if it is an update count or there are no results.

- `executeUpdate()`: Used for DML (Data Manipulation Language) statements like INSERT, UPDATE, DELETE. Returns the number of affected rows.

- `executeQuery()`: Used for SELECT statements. Returns a ResultSet containing the query results.

## Let's Summarize All JDBC Java Code

Here's a summarized version of the JDBC code for quick reference:

```java
public class JdbcDemo {
    static final String JDBC_DRIVER = "com.mysql.cj.jdbc.Driver";
    static final String DB_URL = "jdbc:mysql://localhost/mydatabase";
    static final String USER = "your_username";
    static final String PASS = "your_password";

    public static void main(String[] args) {
        Connection conn = null;
        Statement stmt = null;

        try {
            Class.forName(JDBC_DRIVER);
            conn = DriverManager.getConnection(DB_URL, USER, PASS);
            stmt = conn.createStatement();

            // Perform CRUD operations

        } catch (SQLException se) {
            se.printStackTrace();
        } catch (Exception e) {
            e.printStackTrace ();
        } finally {
            try {
                if (stmt != null) stmt.close();
            } catch (SQLException se) {
                se.printStackTrace();
            }
            try {
                if (conn != null) conn.close();
            } catch (SQLException se) {
                se.printStackTrace();
            }
        }
        System.out.println("Goodbye!");
    }
}
```

## Real Life Software Application Cycle

In real-life software applications, JDBC is used to interact with databases for various tasks, such as user authentication, data storage, and retrieval. The typical software application cycle includes the following steps:

1. User Interaction: Users interact with the application, providing input and receiving output.

2. Data Processing: The application processes the user input and performs various operations, such as data validation and manipulation.

3. Database Interaction: The application interacts with the database using JDBC to store and retrieve data.

4. Display Results: The application displays the processed data and results to the user.

## How We Make Software Cycle

The software development cycle involves several stages:

1. Requirements Gathering: Understanding and gathering the requirements of the software application.

2. Design: Designing the architecture and user interface of the application.

3. Implementation: Writing the code and developing the application.

4. Testing: Testing the application for bugs and errors.

5. Deployment: Deploying the application to the production environment.

6. Maintenance: Maintaining and updating the application as needed.

## Conclusion

JDBC (Java Database Connectivity) is a crucial technology for Java applications to interact with relational databases. It simplifies the process of connecting to databases, executing SQL queries, and processing results. We explored the JDBC architecture, types of drivers, and the basic CRUD operations using JDBC in Java. Understanding JDBC and its capabilities empowers developers to build robust and data-driven Java applications. So go ahead and leverage the power of JDBC to build efficient and dynamic applications for various use cases!
