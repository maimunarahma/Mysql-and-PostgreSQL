# 📘 My Study Notes: MySQL vs PostgreSQL

*A self-learning guide to strengthen understanding of React and frontend concepts.*

---

## 🧠 Table of Contents
- [📌 Introduction](#-introduction)
- [📚 create database](#-create-database)
- [💻CREATE TABLE anf INSERT VALUES(#-code-examples)
- [📎 ALTER (#-cheat-sheet)
- [🔗 Resources](#-resources)
- [✅ To-Do List](#-to-do-list)

---

## 📌 Introduction


---

## 📚 Create Database

To create a database  
```
CREATE DATABASE db_name;
 ```
When working on workbench, its required to call the database using a command  
```
USE DATABASE db_name;
```
insted on code editor like vs code, we can visually edit a database.
```
creating a table  
create table table_name(
  row1_name data_type contraint,
  row2_name data_type contraint
);
```

for inserting a id as a primary key  
mySQL format is:  ```id INT AUTO_INCREMENT PRIMARY KEY  ```
postgreSQL format id : ```id serial primary key  ```

** both sql are case insensitive ,,so uppercase or lowercase command doesn't create any error.

Lets say we create a database name univarsity and create a department table and wanna see the table condition
```
create database univarsity;

create table department(
  id int AUTO_INCREMENT PRIMARY KEY, //for mys1ql format
  id serial PRIMARY KEY, // postgres 
  dept_name char(50) NOT NULL,
  faculty INT(50),
  students INT (500)
);

select * from department; //see department table 
```
insert values into a table
```
insert into department values(1,"CSE',15,450);
```
if any field we want to keep null it can be rewrite as 
```insert into department values(1,'cse','','');```

most used constrains are-``` NOT NULL ,UNIQUE, PRIMARY KEY,FOREIGN KEY ,CHECK```
creating composite primary key
```
CREATE TABLE student(
  id INT(100),
  name char(50) NOT NULL,
phone INT UNIQUE,
email VARCHAR(100) UNIQUE NOT NULL, //using multip[le constrain
PRIMARY KEY(id, email) // creating composite PK
):
```

**uses of ALTER KEY

i)rename a table 
``` ALTER TABLE department RENAME TO DEPT;```

ii)ADD a COLUMN
``` ALTER TABLE tab_name ADD COLUMN col_name constrain;```

iii)DROP COLUMN
```ALTER TABLE tab_name DROP COLUMN col_name;```

iv)RENAME COLUMN
```ALTER TABLE tab_name RENAME COLUMN col_name to update_name;```

v)Constrain Change
```ALTER TABLE tab_name ALTER COLUMN col_name TYPE constrain;```


