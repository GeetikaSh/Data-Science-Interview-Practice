# Types of SQL Commands

SQL commands are categorized into five types based on their functionality:

---

## 1. Data Definition Language (DDL)
DDL commands are used to define and manage the database structure or schema.

| Command       | Description                                 |Syntax|
|---------------|---------------------------------------------|-------|
| `CREATE`      | Creates a new database, table, or index.    |CREATE TABLE table_name (column1 data_type, column2 data_type, ...);|
| `ALTER`       | Modifies an existing database or table.     |ALTER TABLE table_name ADD COLUMN column_name data_type;|
| `DROP`        | Deletes a database, table, or index.        |DROP TABLE table_name|
| `TRUNCATE`    | Removes all records from a table but keeps the structure. |TRUNCATE TABLE table_name;|

---

## 2. Data Manipulation Language (DML)
DML commands are used to manipulate data within the database.

| Command       | Description                                 |Syntax|
|---------------|---------------------------------------------|------|
| `INSERT`      | Adds new records into a table.              |INSERT INTO table_name (column1, column2, ...) VALUES (value1, value2, ...);|
| `UPDATE`      | Modifies existing records in a table.       |UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
| `DELETE`      | Removes specific records from a table.      |DELETE FROM table_name WHERE condition;|

---

## 3. Data Query Language (DQL)
DQL commands are used to query or retrieve data from the database.

| Command       | Description                                 |Syntax|
|---------------|---------------------------------------------|-------|
| `SELECT`      | Retrieves data from one or more tables.     |SELECT column1, column2, ...FROM table_name WHERE condition;|

---

## 4. Data Control Language (DCL)
DCL commands are used to control access to data within the database.

| Command       | Description                                 |
|---------------|---------------------------------------------|
| `GRANT`       | Provides access or privileges to users.     |
| `REVOKE`      | Removes access or privileges from users.    |

---

## 5. Transaction Control Language (TCL)
TCL commands are used to manage transactions in the database.

| Command       | Description                                 |
|---------------|---------------------------------------------|
| `COMMIT`      | Saves all changes made during the transaction. |
| `ROLLBACK`    | Reverts changes made during the transaction.  |
| `SAVEPOINT`   | Sets a point within a transaction to rollback to. |

---

## Summary Table

| Type      | Commands                                     |
|-----------|---------------------------------------------|
| **DDL**   | `CREATE`, `ALTER`, `DROP`, `TRUNCATE`       |
| **DML**   | `INSERT`, `UPDATE`, `DELETE`                |
| **DQL**   | `SELECT`                                    |
| **DCL**   | `GRANT`, `REVOKE`                           |
| **TCL**   | `COMMIT`, `ROLLBACK`, `SAVEPOINT`           |

---

By understanding these SQL command types, you can effectively manage databases, perform data operations, and control user access.

---

# Reference
- [https://www.geeksforgeeks.org/sql-ddl-dql-dml-dcl-tcl-commands/](GeeksforGeeks)
