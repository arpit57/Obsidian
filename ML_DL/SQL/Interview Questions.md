# Queries


## 1.  SELECT: 
The SELECT statement is used to retrieve data from one or more tables.

`SELECT first_name, last_name, age FROM employees;`

## 2.  INSERT: 
The INSERT statement is used to add new records to a table.

`INSERT INTO employees (first_name, last_name, age) VALUES ('John', 'Doe', 30);`

## 3.  UPDATE: 
The UPDATE statement is used to modify existing records in a table.

`UPDATE employees SET age = 31 WHERE first_name = 'John' AND last_name = 'Doe';`

## 4.  DELETE: 
The DELETE statement is used to remove records from a table.

`DELETE FROM employees WHERE first_name = 'John' AND last_name = 'Doe';`

## 5.  JOIN (INNER JOIN): 
The INNER JOIN keyword is used to combine records from two or more tables based on a related column.

`SELECT employees.first_name, employees.last_name, departments.department_name FROM employees INNER JOIN departments ON employees.department_id = departments.department_id;`

## 6.  OUTER JOIN (LEFT JOIN): 
The LEFT JOIN keyword is used to retrieve all records from the left table and matching records from the right table. If no match is found, NULL values are returned for the right table's columns.

`SELECT employees.first_name, employees.last_name, departments.department_name FROM employees LEFT JOIN departments ON employees.department_id = departments.department_id;`

## 7.  GROUP BY: 
The GROUP BY statement is used in conjunction with aggregate functions (COUNT, SUM, AVG, etc.) to group the result set by one or more columns.

`SELECT departments.department_name, COUNT(employees.employee_id) as employee_count FROM employees INNER JOIN departments ON employees.department_id = departments.department_id GROUP BY departments.department_name;`

## 8.  HAVING: 
The HAVING clause is used with the GROUP BY clause to filter the results of an aggregated query based on a specified condition.

`SELECT departments.department_name, COUNT(employees.employee_id) as employee_count FROM employees INNER JOIN departments ON employees.department_id = departments.department_id GROUP BY departments.department_name HAVING employee_count > 10;`

## 9.  SUBQUERY: 
A subquery is a query embedded within another query, often used to filter or retrieve intermediate results.

`SELECT e1.first_name, e1.last_name, e1.salary FROM employees e1 WHERE e1.salary > (     SELECT AVG(e2.salary)     FROM employees e2     WHERE e2.department_id = e1.department_id );`

## 10.  Common Table Expression (CTE): 
A CTE is a temporary result set that can be referenced within a SELECT, INSERT, UPDATE, or DELETE statement.

`WITH sales_cte AS (     SELECT salesperson_id, SUM(sales_amount) as total_sales     FROM sales     GROUP BY salesperson_id ) SELECT s.first_name, s.last_name, c.total_sales FROM salespersons s INNER JOIN sales_cte c ON s.salesperson_id = c.salesperson_id WHERE c.total_sales > 10000;`

# Questions

1.  What are the different types of SQL statements? Can you provide examples for each?
    
2.  Explain the difference between INNER JOIN, OUTER JOIN (LEFT, RIGHT, and FULL), and CROSS JOIN.
    
3.  What is the difference between WHERE and HAVING clauses in SQL? Provide examples.
    
4.  Explain the concept of normalization in database design. Describe the different normal forms (1NF, 2NF, 3NF, BCNF).
    
5.  What are SQL indexes? Explain the differences between clustered and non-clustered indexes, and when to use each type.
    
6.  What are transactions in SQL? Describe the ACID properties and their importance in database systems.
    
7.  What are the different types of subqueries, and how do they work? Provide examples of correlated and non-correlated subqueries.
    
8.  What is a stored procedure, and what are its advantages and disadvantages compared to using regular SQL queries?
    
9.  What are views in SQL, and when should you use them? Explain the difference between a view and a table.
    
10.  Explain the concept of SQL injection and how to prevent it in your queries.
    
11.  What are triggers in SQL? Describe their use cases and potential pitfalls.
    
12.  How do you handle NULL values in SQL? Discuss the use of the COALESCE and NULLIF functions.
    
13.  Describe the process of optimizing SQL queries. What techniques and tools can you use to identify and resolve performance issues?
    
14.  How do you use SQL window functions? Provide examples of using the ROW_NUMBER(), RANK(), and DENSE_RANK() functions.
    
15.  What are Common Table Expressions (CTEs), and how can they be used to improve the readability and maintainability of complex queries?
    
16.  Explain the differences between UNION, UNION ALL, INTERSECT, and EXCEPT operators.
    
17.  How do you manage database schema changes, and what tools or methodologies do you use to handle versioning and migrations?
    
18.  Describe the process of setting up and using SQL Server Reporting Services (SSRS) or a similar reporting tool.
    
19.  Explain the concepts of data warehousing and ETL (Extract, Transform, Load) processes. How do they relate to SQL?
    
20.  How do you handle large datasets and optimize for performance in a real-time, high-transaction environment? Discuss techniques such as partitioning, indexing, and caching.

## Types of SQL statements

a. Data Query Language (DQL) - Used to query and retrieve data from databases. Example: SELECT first_name, last_name FROM employees;

b. Data Definition Language (DDL) - Used to define and manage database structures. Examples:

-   CREATE TABLE employees (id INT, first_name VARCHAR(50), last_name VARCHAR(50));
-   ALTER TABLE employees ADD COLUMN age INT;
-   DROP TABLE employees;

c. Data Manipulation Language (DML) - Used to manipulate data within database tables. Examples:

-   INSERT INTO employees (first_name, last_name) VALUES ('John', 'Doe');
-   UPDATE employees SET age = 30 WHERE first_name = 'John' AND last_name = 'Doe';
-   DELETE FROM employees WHERE first_name = 'John' AND last_name = 'Doe';

d. Data Control Language (DCL) - Used to manage access control and permissions. Examples:

-   GRANT SELECT, INSERT, UPDATE ON employees TO user1;
-   REVOKE DELETE ON employees FROM user1;

e. Transaction Control Language (TCL) - Used to manage transactions within the database. Examples:

-   BEGIN TRANSACTION;
-   COMMIT;
-   ROLLBACK;

## Joins

a. INNER JOIN - Returns records from both tables where there is a match based on the specified condition. Example: SELECT e.first_name, e.last_name, d.department_name FROM employees e INNER JOIN departments d ON e.department_id = d.department_id;

b. OUTER JOIN - Returns records from one or both tables even if there is no match based on the specified condition. There are three types of OUTER JOIN:

-   LEFT JOIN: Returns all records from the left table and matching records from the right table, with NULL values for non-matching rows. Example: SELECT e.first_name, e.last_name, d.department_name FROM employees e LEFT JOIN departments d ON e.department_id = d.department_id;
-   RIGHT JOIN: Returns all records from the right table and matching records from the left table, with NULL values for non-matching rows. Example: SELECT e.first_name, e.last_name, d.department_name FROM employees e RIGHT JOIN departments d ON e.department_id = d.department_id;
-   FULL JOIN: Returns all records from both tables, with NULL values for non-matching rows. Example: SELECT e.first_name, e.last_name, d.department_name FROM employees e FULL JOIN departments d ON e.department_id = d.department_id;

c. CROSS JOIN - Returns the Cartesian product of both tables, meaning it combines each row from the first table with each row from the second table. Example: SELECT e.first_name, e.last_name, d.department_name FROM employees e CROSS JOIN departments d;

## WHERE vs HAVING

-   WHERE clause: Used to filter records before the result set is aggregated (used with SELECT, UPDATE, DELETE). It operates on individual rows. Example: SELECT first_name, last_name FROM employees WHERE age > 30;
    
-   HAVING clause: Used to filter records after the result set is aggregated (used with GROUP BY). It operates on aggregated data. Example: 
  
 ```SQL
 SELECT department_id, COUNT(*) as num_employees FROM employees GROUP BY department_id HAVING num_employees > 10;
```

## Normalization in database design

Normalization is the process of organizing a database to minimize redundancy and improve data integrity. It involves decomposing tables into smaller, related tables and defining relationships between them. There are several normal forms:

a. First Normal Form (1NF) - Each column must contain atomic values, and each row must have a unique identifier (primary key). This eliminates duplicate data and ensures that each piece of information is stored in only one place.

b. Second Normal Form (2NF) - A table is in 2NF if it is in 1NF and all its non-primary key columns are fully dependent on the primary key. This means that each non-primary key column should be related to the whole primary key, not just a part of it (in case of composite primary keys).

c. Third Normal Form (3NF) - A table is in 3NF if it is in 2NF and all its non-primary key columns are non-transitively dependent on the primary key. This means that there should be no functional dependencies between non-primary key columns, ensuring that each non-primary key column is dependent on the primary key only.

d. Boyce-Codd Normal Form (BCNF) - A table is in BCNF if it is in 3NF and for every functional dependency (X → Y), X is a superkey. This further enforces that all determinants (the attributes on the left side of a functional dependency) are candidate keys, further reducing redundancy.

## SQL Indexes

Indexes are database objects that help speed up the retrieval of data from tables. They work like an index in a book, allowing the database to quickly locate specific rows without scanning the entire table. There are two main types of indexes:

a. Clustered Index - A clustered index determines the physical order of data storage in a table. Since the data rows are stored in the same order as the index, there can be only one clustered index per table. Clustered indexes are best suited for columns that are frequently used in range queries or when the data needs to be sorted.

b. Non-Clustered Index - A non-clustered index uses a separate structure to store the index data, with a pointer to the actual data row in the table. Multiple non-clustered indexes can exist for a table, and they are best suited for columns that are frequently used in filtering or join conditions.

When to use each type:

-   Use clustered indexes on columns that are frequently used for range queries or sorting, and on columns with a low percentage of duplicate values, to ensure better performance.
-   Use non-clustered indexes on columns that are often used for filtering or join conditions, and on columns with a high percentage of duplicate values, to avoid storing duplicate index data.

## Transactions in SQL

Transactions are sequences of one or more SQL operations that are executed as a single unit of work. They are used to maintain data consistency and integrity when performing multiple related actions. Transactions follow the ACID properties:

a. Atomicity - A transaction is atomic, which means it is either fully completed or not executed at all. If any operation within a transaction fails, the entire transaction is rolled back, and all changes are undone.

b. Consistency - A transaction ensures that the database remains in a consistent state before and after its execution. The database starts in a consistent state, and after the transaction is completed, it returns to a consistent state.

c. Isolation - Transactions are isolated from each other, which means that the intermediate states of a transaction are not visible to other transactions. This ensures that concurrent transactions do not interfere with each other.

d. Durability - Once a transaction is committed, its changes are permanent, and the system should maintain these changes even in the event of a crash or power loss.

## Types of subqueries

a. Non-Correlated Subquery - A non-correlated subquery is a subquery that is independent of the outer query and can be executed on its own. The result of the subquery is used by the outer query for further processing.
```sql
`SELECT first_name, last_name FROM employees WHERE salary > (     SELECT AVG(salary) FROM employees );`
```

b. Correlated Subquery - A correlated subquery is a subquery that depends on the outer query for its values. The subquery is executed once for each row processed by the outer query.
```SQL
`SELECT e1.first_name, e1.last_name FROM employees e1 WHERE EXISTS (     SELECT 1     FROM employees e2     WHERE e2.manager_id = e1.employee_id );`
```

## Stored Procedures

A stored procedure is a precompiled group of SQL statements that are stored in the database. It can be called by various database clients and can accept input parameters and return output values.

Advantages:

-   Improved performance: Stored procedures are precompiled, which reduces the overhead of query compilation and optimization during runtime.
-   Code reusability: Stored procedures can be called from multiple applications or queries, promoting code reusability and maintainability.
-   Enhanced security: Stored procedures can provide controlled access to data by limiting direct table access and allowing data manipulation only through predefined processes.

Disadvantages:

-   Portability: Stored procedures are often database-specific and may require rewriting when migrating to a different database system.
-   Debugging and maintenance: Debugging stored procedures can be more complex than regular SQL queries, and changes to stored procedures may require updates to all calling applications.

## Views

A view is a virtual table that represents the result of a SELECT query. Views can be used to simplify complex queries, encapsulate business logic, or restrict access to specific columns or rows in a table.

Views should be used when you need to:

-   Simplify complex queries or calculations for easier comprehension.
-   Create reusable query templates.
-   Restrict access to specific data within a table.

Difference between a view and a table:

-   A table is a physical object that stores data, whereas a view is a virtual object that represents the result of a SELECT query.
-   Tables store actual data, while views display data from one or more tables without storing the data themselves.

## SQL Injection

SQL injection is a security vulnerability where an attacker manipulates an SQL query by injecting malicious code, potentially allowing unauthorized access, data manipulation, or data deletion.

## Triggers

Triggers are database objects that automatically execute a predefined set of actions in response to specific events (e.g., INSERT, UPDATE, DELETE) on a specified table or view. They are used for maintaining data consistency, enforcing business rules, and auditing data changes.

Use cases:

-   Enforcing referential integrity and data validation rules.
-   Automatically updating related records or creating new records based on specific events.
-   Auditing changes in data by maintaining a log of actions.

Potential pitfalls:

-   Performance impact: Improper use of triggers can lead to performance issues, as they add extra processing overhead.
-   Complexity: Triggers can make the system more complex and harder to understand, increasing the risk of bugs and maintenance difficulties.
-   Debugging: Debugging and troubleshooting issues related to triggers can be challenging, as they operate behind the scenes.

## Handling Null values

NULL values represent missing or unknown data in SQL. You can handle NULL values using functions like COALESCE and NULLIF:

-   COALESCE: The COALESCE function returns the first non-NULL value in a list of arguments. It can be used to provide a default value when a column contains NULL values. Example: SELECT COALESCE(age, 0) FROM employees;
    
-   NULLIF: The NULLIF function returns NULL if the two specified arguments are equal, otherwise it returns the first argument. It can be used to replace specific values with NULL. Example: SELECT NULLIF(age, -1) FROM employees;

## Optimizing queries

Optimizing SQL queries involves identifying and resolving performance issues to improve query execution time and resource usage. Techniques and tools for optimization include:

-   Using EXPLAIN or EXPLAIN ANALYZE to understand the query execution plan and identify potential bottlenecks.
-   Analyzing database schema and indexing strategy, ensuring that appropriate indexes are in place for frequently queried columns.
-   Rewriting queries to use JOINs instead of subqueries or correlated subqueries, where applicable.
-   Reducing the amount of data retrieved by limiting columns and rows in the SELECT statement.
-   Utilizing database-specific optimization features, such as query hints or materialized views.
-   Monitoring and analyzing database performance using built-in or third-party tools.

## Window functions

Window functions perform calculations across a set of rows related to the current row, without collapsing the rows into a single output. Examples of window functions include ROW_NUMBER(), RANK(), and DENSE_RANK():

-   ROW_NUMBER(): Assigns a unique number to each row within the result set, based on the specified ORDER BY clause. Example: SELECT first_name, last_name, ROW_NUMBER() OVER (ORDER BY salary DESC) as row_number FROM employees;
    
-   RANK(): Assigns a unique rank number to each row within the result set, based on the specified ORDER BY clause. Rows with equal values receive the same rank, and a gap appears in the sequence for the next rank. Example: SELECT first_name, last_name, RANK() OVER (ORDER BY salary DESC) as rank FROM employees;
    
-   DENSE_RANK(): Assigns a unique rank number to each row within the result set, based on the specified ORDER BY clause. Rows with equal values receive the same rank, and no gaps appear in the sequence. Example: SELECT first_name, last_name, DENSE_RANK() OVER (ORDER BY salary DESC) as dense_rank FROM employees;

## Common Table Expressions(CTEs)

Common Table Expressions (CTEs) are temporary, named result sets that can be referenced within a SELECT, INSERT, UPDATE, or DELETE statement. They improve the readability and maintainability of complex queries by breaking them into smaller, more manageable parts.

Example of using a CTE to calculate the average salary per department:

```sql
WITH department_avg_salaries AS (
    SELECT department_id, AVG(salary) AS avg_salary
    FROM employees
    GROUP BY department_id
)
SELECT e.first_name, e.last_name, e.department_id, e.salary, das.avg_salary
FROM employees e
JOIN department_avg_salaries das ON e.department_id = das.department_id;
```

In this example, the CTE `department_avg_salaries` calculates the average salary for each department. The main query then joins the `employees` table with the CTE to display each employee's name, department, salary, and the average salary of their department.

CTEs can be particularly useful for:

-   Simplifying complex queries by breaking them into smaller, more readable parts.
-   Performing recursive queries to traverse hierarchical data structures.
-   Encapsulating reusable subquery logic that is used multiple times within a larger query.
-   Improving performance by materializing intermediate results, which can then be used in multiple places within the query.

## UNION, UNION ALL, INTERSECT, EXCEPT

-   UNION: Combines the result sets of two or more SELECT queries and returns distinct rows from the combined result set. The queries must have the same number of columns and compatible data types. Example: SELECT city FROM customers UNION SELECT city FROM suppliers;
    
-   UNION ALL: Combines the result sets of two or more SELECT queries and returns all rows, including duplicates, from the combined result set. The queries must have the same number of columns and compatible data types. Example: SELECT city FROM customers UNION ALL SELECT city FROM suppliers;
    
-   INTERSECT: Returns only the rows that are common to the result sets of two SELECT queries. The queries must have the same number of columns and compatible data types. Example: SELECT product_id FROM orders WHERE customer_id = 1 INTERSECT SELECT product_id FROM inventory WHERE quantity > 10;
    
-   EXCEPT: Returns the rows from the first SELECT query's result set that do not appear in the second SELECT query's result set. The queries must have the same number of columns and compatible data types. Example: SELECT customer_id FROM orders WHERE order_date < '2021-01-01' EXCEPT SELECT customer_id FROM orders WHERE order_date >= '2021-01-01';

## Managing database schema changes and versioning

Database schema changes can be managed using migration scripts that describe the necessary changes, such as creating or altering tables, indexes, and constraints. Version control systems (e.g., Git) can be used to track these migration scripts.

Tools and methodologies for handling migrations include:

-   Manual scripts: Writing SQL scripts to handle schema changes and applying them in the correct order.
-   Database migration frameworks: Tools like Flyway, Liquibase, or Django Migrations that automate the process of managing and applying migration scripts.
-   Version control branching strategies: Using branching strategies like GitFlow or trunk-based development to manage migration scripts in parallel with application code.

## SQL Server Reporting Services (SSRS)

-   Install and configure the reporting tool (e.g., SSRS) on a server or cloud-based environment.
-   Connect the reporting tool to the desired data sources (e.g., SQL Server, Oracle, etc.).
-   Design and develop reports using the provided tools, such as Report Builder or Visual Studio for SSRS.
-   Deploy the reports to the reporting server, making them accessible to users.
-   Configure security settings, such as user access rights and data source authentication.
-   Schedule report generation and delivery, as needed.

## Data warehousing and ETL processes

Data warehousing is the process of collecting, storing, and managing data from various sources in a central repository for reporting and analysis purposes. ETL (Extract, Transform, Load) processes are used to move and transform data from source systems to the data warehouse.

-   Extract: Data is extracted from various source systems, such as databases, files, or APIs.
-   Transform: Data is cleaned, transformed, and enriched to conform to the data warehouse schema and business requirements.
-   Load: Transformed data is loaded into the data warehouse.

SQL plays a crucial role in ETL processes, as it's used to query, manipulate, and transform data during the extraction and transformation phases, and to load data into the data warehouse.

## Handling large datasets in a high-transaction environment

Handling large datasets and optimizing performance in a real-time, high-transaction environment requires a combination of techniques, such as partitioning, indexing, and caching, along with other strategies:

1.  Partitioning: Split large tables into smaller, more manageable pieces based on a specified column, such as date or a range of values. This can improve query performance by reducing the amount of data that needs to be scanned and allowing for parallel processing.
    
2.  Indexing: Create appropriate indexes to optimize query performance. This may include clustered, non-clustered, or columnstore indexes, depending on the specific use case. Analyze query patterns and identify frequently accessed columns to determine which indexes would be most beneficial.
    
3.  Caching: Store frequently accessed data in memory to reduce the need for repeated, time-consuming database queries. This can be done at the application level using caching mechanisms like Redis or Memcached, or at the database level using features like SQL Server's Buffer Pool Extension.
    
4.  Query optimization: Optimize SQL queries to reduce execution time and resource usage. This can involve rewriting suboptimal queries, using window functions, or leveraging database-specific features like query hints or materialized views.
    
5.  Denormalization: While normalization is important for data integrity, denormalization can improve query performance by reducing the number of joins required. Consider denormalizing data where appropriate to strike a balance between data integrity and performance.
    
6.  Database sharding: Distribute data across multiple database instances to spread the workload and improve performance. Sharding can be particularly helpful in write-heavy environments, where it can help alleviate contention and improve throughput.
    
7.  Connection pooling: Use connection pooling to manage and reuse database connections efficiently, reducing the overhead of establishing new connections for each query.
    
8.  Hardware optimization: Ensure that the underlying hardware (e.g., CPU, memory, storage) is appropriately sized and configured for the workload. Use fast storage solutions like SSDs, and consider utilizing in-memory databases or features like SQL Server's In-Memory OLTP for critical, high-transaction workloads.
    
9.  Monitoring and performance tuning: Regularly monitor database performance using built-in or third-party tools to identify bottlenecks and potential areas for optimization. Continuously fine-tune the system to adapt to changing workloads and requirements.

