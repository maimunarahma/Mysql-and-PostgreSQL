# 📘 My Study Notes: MySQL vs PostgreSQL

*A self-learning guide to strengthen understanding of React and frontend concepts.*

---

## 🧠 Table of Contents
- [📌 Introduction](#-introduction)
- [📚 create database](#-create-database)
- [💻 Code Examples](#-code-examples)
- [📎 Cheat Sheet](#-cheat-sheet)
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
