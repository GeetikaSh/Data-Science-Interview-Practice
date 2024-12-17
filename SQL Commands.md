# Types of SQL Commands

SQL commands are categorized into five types based on their functionality:

---

## 1. Data Definition Language (DDL)
DDL commands are used to define and manage the database structure or schema.

| Command       | Description                                 |
|---------------|---------------------------------------------|
| `CREATE`      | Creates a new database, table, or index.    |
| `ALTER`       | Modifies an existing database or table.     |
| `DROP`        | Deletes a database, table, or index.        |
| `TRUNCATE`    | Removes all records from a table but keeps the structure. |

---

## 2. Data Manipulation Language (DML)
DML commands are used to manipulate data within the database.

| Command       | Description                                 |
|---------------|---------------------------------------------|
| `INSERT`      | Adds new records into a table.              |
| `UPDATE`      | Modifies existing records in a table.       |
| `DELETE`      | Removes specific records from a table.      |

---

## 3. Data Query Language (DQL)
DQL commands are used to query or retrieve data from the database.

| Command       | Description                                 |
|---------------|---------------------------------------------|
| `SELECT`      | Retrieves data from one or more tables.     |

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
