# MySQL-study
Reference material for the use of MySQL within VScode

# Glossary of SQL Keywords

**1. SELECT:** Used to select data from a database. The data returned is stored in a result table, called the result-set.

Example: `SELECT column1, column2 FROM table_name;`

**2. FROM:** Used in conjunction with SELECT to specify the table from which to retrieve the data.

Example: `SELECT * FROM Customers;`

**3. WHERE:** Used to filter records.

Example: `SELECT * FROM Customers WHERE Country='Mexico';`

**4. INSERT INTO:** Used to insert new data into a table.

Example: `INSERT INTO Customers (CustomerName, ContactName, Country) VALUES ('Cardinal','Tom B. Erichsen','Norway');`

**5. UPDATE:** Used to modify the existing records in a table.

Example: `UPDATE Customers SET ContactName='Alfred Schmidt', City='Hamburg' WHERE CustomerName='Alfreds Futterkiste';`

**6. DELETE:** Used to delete existing records in a table.

Example: `DELETE FROM Customers WHERE CustomerName='Alfreds Futterkiste';`

**7. CREATE DATABASE:** Used to create a new database.

Example: `CREATE DATABASE testDB;`

**8. ALTER DATABASE:** Used to modify a database.

Example: `ALTER DATABASE database_name COLLATE new_collation_name;`

**9. CREATE TABLE:** Used to create a new table.

Example: `CREATE TABLE Customers (CustomerID int, CustomerName varchar(255));`

**10. ALTER TABLE:** Used to add, delete/drop or modify columns in an existing table.

Example: `ALTER TABLE Customers ADD Email varchar(255);`

**11. DROP TABLE:** Used to delete a table.

Example: `DROP TABLE Customers;`

**12. CREATE INDEX:** Used to create an index (search key).

Example: `CREATE INDEX idx_lastname ON Customers (LastName);`

**13. DROP INDEX:** Used to delete an index.

Example: `ALTER TABLE table_name DROP INDEX index_name;`

**14. JOIN:** Used to combine rows from two or more tables, based on a related column between them.

Example: `SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate FROM Orders INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID;`

**15. UNION:** Used to combine the result from multiple SELECT statements (removes duplicate rows).

Example: `SELECT column_name(s) FROM table1 UNION SELECT column_name(s) FROM table2;`

**16. GROUP BY:** Often used with aggregate functions (COUNT, MAX, MIN, SUM, AVG) to group the result-set by one or more columns.

Example: `SELECT COUNT(CustomerID), Country FROM Customers GROUP BY Country;`

**17. ORDER BY:** Used to sort the result-set in ascending or descending order.

Example: `SELECT * FROM Customers ORDER BY Country;`

**18. LIMIT:** Used to specify the number of records to return in the result set.

Example: `SELECT * FROM Customers LIMIT 3;`

**19. COUNT:** An aggregate function that returns the number of rows that matches a specified criterion.

Example: `SELECT COUNT(column_name) FROM table_name;`

**20. AVG:** An aggregate function that returns the average value of a numeric column.

Example: `SELECT AVG(column_name) FROM table_name;`

**21. SUM:** An aggregate function that returns the total sum of a numeric column.

Example: `SELECT SUM(column_name) FROM table_name;`

**22. LIKE:** Used in a WHERE clause to search for a specified pattern in a column.

Example: `SELECT * FROM Customers WHERE CustomerName LIKE 'a%';`

**23. BETWEEN:** Used in a WHERE clause to filter

 the result within a certain range. The values can be numbers, text, or dates.

Example: `SELECT * FROM Products WHERE Price BETWEEN 10 AND 20;`

These are some common SQL keywords. Each SQL statement in your program must contain a keyword to tell the SQL what you want to do, and this can range from adding data, manipulating data, or retrieving data from your database.

# Basics
Let's start with the basics of MySQL:

**What is MySQL?**
MySQL is an open-source relational database management system (RDBMS). It uses Structured Query Language (SQL) for manipulating and managing data stored in relational databases.

**Setting Up MySQL Database in VSCode**
To work with MySQL databases in VSCode, you'd typically want to use a MySQL extension. One popular option is "MySQL" by Jun Han. You can install it from the Extensions view (`Ctrl+Shift+X` to open it).

1. **Installing the Extension:** Type "MySQL" into the Extensions view search box, find the one by Jun Han, and click Install.

2. **Adding a MySQL Connection:** Click on the MySQL icon in the Activity Bar on the side, then click the "+" button to add a new connection. Enter your MySQL server's information and save it.

Now you're ready to interact with your MySQL database from within VSCode.

**Creating a MySQL Database**
You can create a new MySQL database with the `CREATE DATABASE` statement. Here's an example:

```sql
CREATE DATABASE my_database;
```

This SQL statement creates a new database named "my_database".

**Creating a Table**
You can create a new table in your database using the `CREATE TABLE` statement:

```sql
CREATE TABLE Users (
    ID INT AUTO_INCREMENT,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    Email VARCHAR(100),
    PRIMARY KEY (ID)
);
```

This statement creates a new table named "Users" with four columns: "ID", "FirstName", "LastName", and "Email". 

The "ID" column is of type INT and auto-increments with each new record. The "FirstName", "LastName", and "Email" columns are of type VARCHAR with different lengths. The "ID" column is also set as the primary key of the table.

You can run these SQL statements directly from VSCode. Open a new SQL file (`Ctrl+N` and then `Ctrl+K M` and type SQL), write your SQL code, then use `Ctrl+Alt+E` (or right click in the SQL file and choose `Execute Query`) to execute it.

# Data insertion and manipulation

**Inserting Data Into a Table**

You can add data to your table using the `INSERT INTO` statement:

```sql
INSERT INTO Users (FirstName, LastName, Email) 
VALUES ('John', 'Doe', 'john.doe@example.com');
```

This SQL statement inserts a new row into the "Users" table. The `INSERT INTO` clause specifies the table and the columns to insert data into. The `VALUES` clause specifies the data to insert. In this case, 'John' is inserted into the "FirstName" column, 'Doe' into the "LastName" column, and 'john.doe@example.com' into the "Email" column.

**Selecting Data From a Table**

You can retrieve data from your table using the `SELECT` statement:

```sql
SELECT * FROM Users;
```

This SQL statement selects all data from the "Users" table. The `*` wildcard means "all columns". If you want to select data from specific columns, you can specify the column names, like so:

```sql
SELECT FirstName, Email FROM Users;
```

This SQL statement selects data from the "FirstName" and "Email" columns of the "Users" table.

**Where Clause**

The `WHERE` clause is used to filter records:

```sql
SELECT * FROM Users WHERE FirstName = 'John';
```

This SQL statement selects all data from the "Users" table where the "FirstName" is 'John'.

**Updating Data in a Table**

The `UPDATE` statement is used to modify existing records in a table:

```sql
UPDATE Users SET Email = 'new.email@example.com' WHERE FirstName = 'John';
```

This SQL statement updates the "Email" of the user where the "FirstName" is 'John'.

**Deleting Data From a Table**

The `DELETE` statement is used to remove existing records in a table:

```sql
DELETE FROM Users WHERE FirstName = 'John';
```

This SQL statement deletes all records from the "Users" table where the "FirstName" is 'John'. Be careful with the `DELETE` statement, especially without a `WHERE` clause, as it can remove all records from your table.

Again, all these SQL statements can be executed directly from your VSCode SQL file using `Ctrl+Alt+E` or `Execute Query` from the right-click context menu. Always remember to save and backup your data regularly to prevent accidental loss.

# Advanced Concepts

**Join Operations**

Join operations are used to combine rows from two or more tables, based on a related column between them. Here's an example of an `INNER JOIN`:

```sql
SELECT Orders.OrderID, Customers.CustomerName
FROM Orders
INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID;
```

In the above SQL statement, `INNER JOIN` is used to combine rows from the "Orders" and "Customers" tables where the "CustomerID" matches. 

There are various types of joins in SQL:

- `INNER JOIN`: Returns records that have matching values in both tables.
- `LEFT JOIN` (or `LEFT OUTER JOIN`): Returns all records from the left table, and the matched records from the right table. If there is no match, the result is `NULL` on the right side.
- `RIGHT JOIN` (or `RIGHT OUTER JOIN`): Returns all records from the right table, and the matched records from the left table. If there is no match, the result is `NULL` on the left side.
- `FULL JOIN` (or `FULL OUTER JOIN`): Returns all records when there is a match in either left or right table. If there is no match, the result is `NULL` on both sides.

**Subqueries**

A subquery is a query that is nested inside another query. A subquery can return data that will be used in the main query as a condition to further restrict the data to be retrieved. Here's an example:

```sql
SELECT CustomerName, City
FROM Customers
WHERE CustomerID IN (SELECT CustomerID FROM Orders WHERE OrderDate = '2000-01-01');
```

In this SQL statement, the inner query (`SELECT CustomerID FROM Orders WHERE OrderDate = '2000-01-01'`) retrieves the IDs of customers who placed an order on '2000-01-01'. The outer query then retrieves the names and cities of those customers.

**Aggregate Functions**

Aggregate functions perform a calculation on a set of values and return a single value. MySQL provides several aggregate functions including `AVG()`, `COUNT()`, `SUM()`, `MAX()`, and `MIN()`. Here's an example of the `COUNT()` function:

```sql
SELECT COUNT(CustomerID)
FROM Customers;
```

This SQL statement counts and returns the number of customer IDs in the "Customers" table.

# Primary keys and Foreign key relationships

**Primary Keys**

A primary key is a column (or a combination of columns) in a table that uniquely identifies each row of the table. In other words, you cannot have duplicate values in a primary key column. Here is an example of creating a table with a primary key:

```sql
CREATE TABLE Customers (
    CustomerID int NOT NULL,
    CustomerName varchar(255),
    ContactName varchar(255),
    Country varchar(255),
    PRIMARY KEY (CustomerID)
);
```

In this example, the `CustomerID` column is the primary key, so it must contain unique, non-null values.

**Foreign Keys**

A foreign key is a column or a set of columns in a table that is used to establish a link between the data in two tables. It acts as a cross-reference between tables because it references the primary key of another table, thereby establishing a link between them. Here is an example of creating a table with a foreign key:

```sql
CREATE TABLE Orders (
    OrderID int NOT NULL,
    OrderNumber int,
    CustomerID int,
    PRIMARY KEY (OrderID),
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```

In this example, the `CustomerID` in the Orders table is a foreign key that refers to the `CustomerID` in the Customers table. This means that for each order, we store the ID of the customer who made the order, and this allows us to link each order with a specific customer.

**Relationships in MySQL**

In MySQL, relationships can be established between tables by using primary keys and foreign keys. These relationships can be of various types, including:

1. **One-to-One:** Each row in table A is linked to no more than one row in table B. This is often used when you have two tables that have a clear correspondence but are separated because of the nature of the data.

2. **One-to-Many (or Many-to-One):** Each row in table A can be related to many rows in table B. This is the most common relationship type. For example, a customer can have many orders, thus forming a one-to-many relationship.

3. **Many-to-Many:** Multiple rows in table A can be related to multiple rows in table B. Many-to-Many relationships are implemented using a junction table with the keys from both the tables forming the composite primary key of the junction table. 

These relationships establish a link between the data in different tables, thereby allowing complex queries across multiple tables. Understanding and properly designing these relationships are key to a well-functioning relational database system.

let's proceed to the examples. 

**One-to-One Relationship**

Suppose you have a User table and a Profile table, and each User has exactly one Profile.

First, we create the User table:

```sql
CREATE TABLE Users (
    UserID int NOT NULL,
    UserName varchar(255),
    PRIMARY KEY (UserID)
);
```

Then we create the Profile table with UserID as a foreign key:

```sql
CREATE TABLE Profiles (
    ProfileID int NOT NULL,
    UserID int,
    Bio varchar(255),
    PRIMARY KEY (ProfileID),
    FOREIGN KEY (UserID) REFERENCES Users(UserID)
);
```

In this example, `UserID` serves as a foreign key in the `Profiles` table that links to the `UserID` in the `Users` table, establishing a one-to-one relationship.

**One-to-Many Relationship**

Now let's assume that each User can have multiple Orders. Here we have a one-to-many relationship between Users and Orders.

First, we create the Users table as above:

```sql
CREATE TABLE Users (
    UserID int NOT NULL,
    UserName varchar(255),
    PRIMARY KEY (UserID)
);
```

Next, we create the Orders table:

```sql
CREATE TABLE Orders (
    OrderID int NOT NULL,
    UserID int,
    OrderDetails varchar(255),
    PRIMARY KEY (OrderID),
    FOREIGN KEY (UserID) REFERENCES Users(UserID)
);
```

Here, `UserID` is a foreign key in the `Orders` table linking to the `UserID` in the `Users` table. A single user can have multiple orders, forming a one-to-many relationship.

**Many-to-Many Relationship**

Suppose each User can be enrolled in multiple Courses, and each Course can have multiple Users. This is a many-to-many relationship and is implemented via a junction table.

First, we create the Users and Courses tables:

```sql
CREATE TABLE Users (
    UserID int NOT NULL,
    UserName varchar(255),
    PRIMARY KEY (UserID)
);

CREATE TABLE Courses (
    CourseID int NOT NULL,
    CourseName varchar(255),
    PRIMARY KEY (CourseID)
);
```

Then we create a junction table called `UserCourses` to link Users and Courses:

```sql
CREATE TABLE UserCourses (
    UserID int,
    CourseID int,
    PRIMARY KEY (UserID, CourseID),
    FOREIGN KEY (UserID) REFERENCES Users(UserID),
    FOREIGN KEY (CourseID) REFERENCES Courses(CourseID)
);
```

In the `UserCourses` table, both `UserID` and `CourseID` together form the primary key. This allows for each User to be associated with multiple Courses, and each Course to be associated with multiple Users.

These examples should give you a good understanding of how to implement different types of relationships using primary and foreign keys in MySQL.



