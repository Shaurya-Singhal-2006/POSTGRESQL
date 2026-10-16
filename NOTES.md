# 🐘 PostgreSQL Commands

> [!IMPORTANT]
>
> ### 🔑 Change Username and Password
>
> * Replace `newname` with your desired username.
> * Replace `newpass` with your desired password.

### 👤 Create a User

Run in `psql`:

```sql
CREATE ROLE newname WITH LOGIN SUPERUSER PASSWORD 'newpass';
```

### ⚙️ Set Environment Variables

Run in the Windows terminal:

```bash
setx PGUSER newname
setx PGDATABASE postgres
```

### 🔒 Change Password

Run in `psql`:

```sql
ALTER ROLE newname WITH PASSWORD 'newpass';
```

---

# 💡 Quick Tips

> [!NOTE]
>
> * **SQL commands** are used to create, modify, and retrieve database data.
> * **`psql` commands** such as `\l`, `\c`, and `\d` are used inside the PostgreSQL terminal.
> * SQL commands generally end with a semicolon (`;`).
> * Use `\q` to exit `psql`.


---

# 🛠️ Basic Commands

### 🔍 Check PostgreSQL Version

```bash
psql --version
```

### 🗄️ List All Databases

```psql
\l
```

### ➕ Create a Database

```sql
CREATE DATABASE database_name;
```

### 🗑️ Delete a Database

> [!WARNING]
> This permanently deletes the specified database.

```sql
DROP DATABASE database_name;
```

### 🔗 Connect to a Database

**Using the terminal:**

```bash
psql -h localhost -p 5432 -U username database_name
```

**Inside `psql`:**

```psql
\c database_name
```

### 📚 View Help

```bash
psql --help
```

---

# 📋 Working with Tables

### 🏗️ Create a Table

```sql
CREATE TABLE person (
    id INT,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    gender VARCHAR(7),
    date_of_birth DATE
);
```

### 🔎 Get Table Information

```psql
\d table_name
```

### 🔐 Create a Table with Constraints

* `BIGSERIAL` → Automatically generates sequential IDs.
* `PRIMARY KEY` → Ensures each record has a unique, non-null ID.
* `NOT NULL` → Prevents `NULL` values.

```sql
CREATE TABLE person (
    id BIGSERIAL PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    gender VARCHAR(7) NOT NULL,
    date_of_birth DATE NOT NULL
);
```

### ❌ Delete a Table

> [!WARNING]
> This deletes the table and all its data.

```sql
DROP TABLE table_name;
```

---

# ✍️ Inserting Data

### ➕ Insert a Record

```sql
INSERT INTO person (
    first_name,
    last_name,
    gender,
    date_of_birth
)
VALUES (
    'Shaurya',
    'Singhal',
    'MALE',
    DATE '2006-11-09'
);
```

### 🎲 Insert 1,000 Rows Using Mockaroo

Generate sample data using [Mockaroo](https://www.mockaroo.com/) and download it in SQL format.

Run this command inside `psql` to execute the file:

```psql
\i 'D:/path/to/file.sql'
```

> [!TIP]
> Replace the example path with the actual location of your SQL file.

---

# 📊 Retrieving Data

### 👀 View All Records

The `*` symbol represents all columns in a table.

```sql
SELECT * FROM person;
```

### 🎯 Select Specific Columns

Retrieve only the columns you need.

```sql
SELECT first_name, last_name
FROM person;
```

---
# Sorting Data