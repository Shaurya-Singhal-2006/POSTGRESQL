# 🚨 VERY IMPORTANT !!!

> [!IMPORTANT]
> ### 🔑 TO CHANGE USER NAME
>
> - Change `'newpass'` to the password you want.
> - Change `'newname'` to the username you want.

### 🖥️ Run This in psql

```psql
CREATE ROLE newname WITH LOGIN SUPERUSER PASSWORD 'newpass';
```

### 💻 Run This in Terminal

```bash
setx PGUSER newname

setx PGDATABASE postgres
```

### 🖥️ Run This in psql

```psql
ALTER ROLE newname WITH PASSWORD 'newpass';
```

---

<br>

# 📝 NOTES

- ### Check PostgreSQL Version

```bash
psql --version 
```

---

- ### List All Databases

```bash
\l
```

---

- ### Create Database

```bash
CREATE DATABASE [NAME];
```

---

- ### Delete Database ⚠️

> [!WARNING]
> **Be careful!** This command deletes the specified database.

```psql
DROP DATABASE [NAME];
```

---

- ### Connect to Database

#### 🔹 First Way — Using Terminal

```bash
psql -h localhost -p 5432 -U [user_name] [database_name]
```

#### 🔹 Second Way — Using psql

```psql
\c [database_name]
```

---

- ### More Commands 📚

```bash
psql --help
```

---

- ### Create a Table
#### EXAMPLE

```psql
CREATE TABLE person (
    id INT,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    gender VARCHAR(7),
    date_of_birth DATE );
```

---

- ### Get Info About The Table
```psql
\d [table_name]
```
---

- ### Create Table With Constraints

> [!NOTE]
>- `BIGSERIAL` automatically generates sequential IDs when a value is not explicitly provided.
>- `PRIMARY KEY` ensures that each ID is unique and cannot be `NULL`.
>- `VARCHAR(50)` allows text up to 50 characters long.
>- `DATE` stores dates in the format `YYYY-MM-DD`.
>- `NOT NULL` means a value must be provided for that column.

<br>

```psql
CREATE TABLE person (
    id BIGSERIAL NOT NULL PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    gender VARCHAR(7) NOT NULL,
    date_of_birth DATE NOT NULL );
```

---

- ### Delete a Table

> [!WARNING]
>**Be careful!** This command deletes the specified table.

```psql
DROP TABLE [table_name];
```

---

- ### Insert Records Into Table
#### Example 
```psql
INSERT INTO person (
    first_name,
    second_name,
    gender,
    date_of_birth )

    [click enter]

    VALUES ('Shaurya','Singhal','MALE', date '2006-11-09');
```

---

- ### Insert 1000 Rows with Mockaroo

>[!NOTE] Go to LINK  : ` https://www.mockaroo.com/ ` <br>
> To generate the data <br>
> Download it in SQL format 

- #### Use
```psql
\i [file_location] 
```