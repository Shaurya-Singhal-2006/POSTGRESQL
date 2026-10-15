# PostgreSQL Commands and Notes

> [!IMPORTANT]
> **To Change the Username and Password**
>
> * Replace `newname` with the username you want.
> * Replace `newpass` with the password you want.
> * Run the commands in the appropriate environment as specified below.

### Create a New User

**Run this command in `psql`** to create a new PostgreSQL user with login and superuser privileges.

```sql
CREATE ROLE newname WITH LOGIN SUPERUSER PASSWORD 'newpass';
```

> [!WARNING]
> A superuser has extensive privileges over the PostgreSQL server. Only grant superuser access to trusted accounts.

### Set Environment Variables

**Run these commands in the Windows terminal** to set the default PostgreSQL username and database.

```bash
setx PGUSER newname
setx PGDATABASE postgres
```

> [!NOTE]
> The `setx` command saves environment variables for future terminal sessions. Close and reopen the terminal for the changes to take effect.

### Change the User Password

**Run this command in `psql`** to update the password of an existing user.

```sql
ALTER ROLE newname WITH PASSWORD 'newpass';
```

---

# PostgreSQL Basics

### Check PostgreSQL Version

Use this command in the terminal to check the installed PostgreSQL client version.

```bash
psql --version
```

### List All Databases

Use this command inside `psql` to display all databases on the PostgreSQL server.

```psql
\l
```

### Create a Database

Use `CREATE DATABASE` to create a new database. Replace `[database_name]` with your desired database name.

```sql
CREATE DATABASE database_name;
```

### Delete a Database

Use `DROP DATABASE` to permanently delete a database.

> [!WARNING]
> This command deletes the specified database and its contents. Make sure you select the correct database before executing it.

```sql
DROP DATABASE database_name;
```

### Connect to a Database

There are two ways to connect to a PostgreSQL database.

**First Way — Using the Terminal**

Use this command to connect to a database by specifying the host, port, username, and database name.

```bash
psql -h localhost -p 5432 -U username database_name
```

* `-h localhost`: Specifies the database server.
* `-p 5432`: Specifies the PostgreSQL port.
* `-U username`: Specifies the PostgreSQL username.
* `database_name`: Specifies the database to connect to.

**Second Way — Using `psql`**

If you are already connected to a PostgreSQL server through `psql`, use `\c` to switch databases.

```psql
\c database_name
```

### Get Help

Use this command in the terminal to view the available `psql` command-line options.

```bash
psql --help
```

---

# Working with Tables

### Create a Table

Use `CREATE TABLE` to create a table with the required columns and data types.

**Example: Creating a `person` Table**

```sql
CREATE TABLE person (
    id INT,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    gender VARCHAR(7),
    date_of_birth DATE
);
```

**Column descriptions:**

* `id INT`: Stores an integer ID.
* `first_name VARCHAR(50)`: Stores a first name of up to 50 characters.
* `last_name VARCHAR(50)`: Stores a last name of up to 50 characters.
* `gender VARCHAR(7)`: Stores text of up to 7 characters.
* `date_of_birth DATE`: Stores a date.

### Get Information About a Table

Use `\d` to view a table's structure, including its columns, data types, and constraints.

Replace `[table_name]` with the name of your table.

```psql
\d table_name
```

### Create a Table with Constraints

Constraints help maintain data accuracy and integrity.

* `BIGSERIAL`: Automatically generates sequential integer IDs when a value is not explicitly provided.
* `PRIMARY KEY`: Ensures that each row has a unique, non-null identifier.
* `VARCHAR(50)`: Allows text of up to 50 characters.
* `DATE`: Stores dates in the format `YYYY-MM-DD`.
* `NOT NULL`: Prevents a column from containing `NULL` values.

**Example:**

```sql
CREATE TABLE person (
    id BIGSERIAL PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    gender VARCHAR(7) NOT NULL,
    date_of_birth DATE NOT NULL
);
```

> [!NOTE]
> `BIGSERIAL` uses an underlying sequence to generate IDs. It does not automatically guarantee uniqueness by itself; the `PRIMARY KEY` constraint enforces uniqueness.

### Delete a Table

Use `DROP TABLE` to permanently remove a table and its data.

> [!WARNING]
> This command deletes the specified table. Make sure you do not need its data before executing it.

```sql
DROP TABLE table_name;
```

---

# Inserting Data

### Insert a Record into a Table

Use `INSERT INTO` to add a new record to a table.

Specify the column names first, followed by the values to insert.

**Example:**

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

> [!NOTE]
> The column name is `last_name`, not `second_name`, because that is how the column was defined in the table.

### Insert 1,000 Rows Using Mockaroo

[Mockaroo](https://www.mockaroo.com/) is an online tool that generates realistic sample data for testing and practice.

**Steps:**

* Open [Mockaroo](https://www.mockaroo.com/).
* Configure the fields according to your table structure.
* Generate the required number of records.
* Download the data in SQL format.
* Open `psql` and execute the downloaded SQL file using the command below.

**Run this command inside `psql`:**

```psql
\i 'D:/path/to/your/file.sql'
```

Replace the example path with the actual location of your downloaded SQL file.

> [!TIP]
> In PostgreSQL's `psql`, the `\i` command executes SQL commands from a file. On Windows, forward slashes (`/`) can be used in file paths to avoid backslash-related issues.

---

# Retrieving Data

### View All Records from a Table

Use `SELECT *` to retrieve all columns and rows from a table.

```sql
SELECT * FROM person;
```

Here, `*` represents all columns in the table.

### Select Specific Columns

If you only need certain columns, specify their names instead of using `*`.

**Example: Retrieve First and Last Names**

```sql
SELECT first_name, last_name
FROM person;
```

This query displays only the `first_name` and `last_name` columns for all records in the `person` table.
