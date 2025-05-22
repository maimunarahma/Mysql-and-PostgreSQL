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



***USES of SELECT Queries

i) to show all columns of a table without data
``` SELECT FROM tab-name;```

ii) show all columns of table with data
``` SELECT * FROM tab_name;```

iii) show specific columns
```SELECT col1_name, col2_name FROM tab_name;```
```SELECT col1_name as custom_name FROM tab_name; //visualize a column with a customize name```

iv)filter using SELECT query
 ```ORDER BY col_name ASC ```
 ```ORDER BY col_name DESC```
 ```SELECT * FROM department ORDER BY students ASC; //show all datta of department table with ascending order of students column```
 
 v) DISTINCT
 ``` SELECT DISTINCT location from student //show all distinct values of location column in student table```
 
vi)WHERE ,AND,OR 


## 📚 Scalar Function vs Agregate Function
 Scalar function: operates on each vales of the corresponding column and return value for each of the column.
 ```SELECT concat(first_name,' '.last_name) from students;```

 ```SELECT length(first_name) from students;```

 Agregate Function: operates on whole column values and retruns a single value;  

 ```SELECT avg(age) from students;```
 
 ``` SELECT coutn(*) from student;  ///retun count of rows ,number of data containing the table```

 ```SELECT max(mark) from student;```

 ``` SELECT min(age) from student;``` 

 ``` SELECT sum(age) from student;```

 ## Understanding NULL
 If we wanna filter null values of a column using WHERE operator, it will return nothing.As where operator outputs only when the conditional expression is either true or false.
 Suppose inb my student table ,I have email column which can be null or not null .
 so if we run this command like 

 ```SELECT * from students WHERE email=NULL;``` 
 it will true for some row and false for some row. so this expressin is wrong.Instead this, in case of NULL we need to use IS or IS NOT.
 such as:

 ```SELECT * FROM students WHERE email IS NULL; //returns all columns where email is null```

  ```SELECT * FROM students WHERE email IS NOT NULL;   //returns all columns where email is not null```

###

### IN ,BETWEEN ,LIKE operator
if we want to filter all datas of students location.
```SELECT * from student WHERE home='dhaka' OR home='JASHORE' OR home='khulna'; ```

```SELECT  * from student WHERE home IN('dhaka','JASHORE','khulna');```
both mean same thing.

```SELECT  * from student WHERE home NOT IN('dhaka','JASHORE','khulna');```
using NOT operator we can get opposite values

**BETWEEN

```SELECT * from student WHERE age 20 and 25;```
outputs all datas filtering age columns value 20-25


### LIMIT and OFFSET
Limit operator indicate how many datas will output. 
and offset indicate from nth value's data ,,indicate the initial datas position
```SELECT  * from student```
```WHERE home IN('dhaka','JASHORE','khulna') LIMIT 5 OFFSET 3;  //(3+1)th data theke prothom 5 ta data dekhabe ei condition satisfy kore```

these two operator handles pagination 
### DELETE , UPDATE
```UPDATE student set email='default@gmail.com' where email is NULL;```
