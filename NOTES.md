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

## 🚀 INTRO

---

### 1️⃣ Check PostgreSQL Version

```bash
psql --version 
```

---

### 2️⃣ List All Databases

```bash
\l
```

---

### 3️⃣ Create Database

```bash
CREATE DATABASE [NAME];
```

---

### 4️⃣ Delete Database ⚠️

> [!WARNING]
> **Be careful!** This command deletes the specified database.

```psql
DROP DATABASE [NAME];
```

---

### 5️⃣ Connect to Database

#### 🔹 First Way — Using Terminal

```bash
psql -h localhost -p 5432 -U [user_name] [database_name]
```

#### 🔹 Second Way — Using psql

```psql
\c [database_name]
```

---

### 6️⃣ More Commands 📚

```bash
psql --help
```

---