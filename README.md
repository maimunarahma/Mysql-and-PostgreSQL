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
### UPDATE
Only changes data inside table rows (the values).

You can update one or multiple columns’ values for one or many rows.

Does NOT change table structure.


### ALTER
Changes the table structure (schema).

Can add, remove, rename columns, or change properties of existing columns like:

Data type

Constraints (e.g., primary key, foreign key, unique)

Default values

Nullability (allow or disallow NULL)

Does NOT change the actual data values inside rows (except when changing data type might cause implicit conversions).



### Command	What it changes
UPDATE	Data inside existing columns

ALTER	Structure or definition of columns (schema)

### All ALTER command of mysql and postgresql 

| Operation                 | MySQL Syntax Example                                          | PostgreSQL Syntax Example                                   | Notes & Differences                                |
|---------------------------|---------------------------------------------------------------|------------------------------------------------------------|---------------------------------------------------|
| **Add column**             | `ALTER TABLE table_name ADD COLUMN col_name datatype;`        | `ALTER TABLE table_name ADD COLUMN col_name datatype;`     | Same syntax                                      |
| **Drop column**            | `ALTER TABLE table_name DROP COLUMN col_name;`                | `ALTER TABLE table_name DROP COLUMN col_name;`             | Same syntax                                      |
| **Rename table**           | `RENAME TABLE old_name TO new_name;`                          | `ALTER TABLE old_name RENAME TO new_name;`                  | PostgreSQL uses ALTER TABLE                        |
| **Rename column**          | `ALTER TABLE table_name CHANGE COLUMN old_name new_name datatype;` | `ALTER TABLE table_name RENAME COLUMN old_name TO new_name;` | MySQL requires datatype with rename               |
| **Modify/change column type** | `ALTER TABLE table_name MODIFY COLUMN col_name new_datatype;` | `ALTER TABLE table_name ALTER COLUMN col_name TYPE new_datatype;` | Syntax differs                                    |
| **Set default value**      | `ALTER TABLE table_name ALTER COLUMN col_name SET DEFAULT value;` | `ALTER TABLE table_name ALTER COLUMN col_name SET DEFAULT value;` | Same syntax                                      |
| **Drop default value**     | `ALTER TABLE table_name ALTER COLUMN col_name DROP DEFAULT;`  | `ALTER TABLE table_name ALTER COLUMN col_name DROP DEFAULT;` | Same syntax                                      |
| **Add primary key**        | `ALTER TABLE table_name ADD PRIMARY KEY (col_name);`          | `ALTER TABLE table_name ADD PRIMARY KEY (col_name);`       | Same syntax                                      |
| **Drop primary key**       | `ALTER TABLE table_name DROP PRIMARY KEY;`                     | `ALTER TABLE table_name DROP CONSTRAINT constraint_name;`  | PG requires constraint name                       |
| **Add foreign key**        | `ALTER TABLE table_name ADD CONSTRAINT fk_name FOREIGN KEY (col) REFERENCES ref_table(ref_col);` | Same as MySQL                                     | Same syntax                                      |
| **Drop foreign key**       | `ALTER TABLE table_name DROP FOREIGN KEY fk_name;`             | `ALTER TABLE table_name DROP CONSTRAINT fk_name;`          | PG drops constraint by name                       |
| **Change column nullability** | `ALTER TABLE table_name MODIFY COLUMN col_name datatype [NOT NULL | NULL];` | `ALTER TABLE table_name ALTER COLUMN col_name SET NOT NULL;` <br>or <br> `ALTER TABLE table_name ALTER COLUMN col_name DROP NOT NULL;` | Syntax differs                                    |
| **Change column comment**  | `ALTER TABLE table_name MODIFY COLUMN col_name datatype COMMENT 'comment';` | `COMMENT ON COLUMN table_name.col_name IS 'comment';`      | Syntax very different                             |
| **Change column order**    | `ALTER TABLE table_name MODIFY COLUMN col_name datatype AFTER other_col;` | Not supported                                             | MySQL supports, PG does not                       |


### UPDATE commands of sql and postgresql 

### 📝 UPDATE Command Comparison: MySQL vs PostgreSQL

| Operation                          | MySQL Syntax Example                                               | PostgreSQL Syntax Example                                            | Notes & Differences                                               |
|-----------------------------------|---------------------------------------------------------------------|----------------------------------------------------------------------|-------------------------------------------------------------------|
| **Update one column (all rows)**   | `UPDATE users SET age = 30;`                                        | `UPDATE users SET age = 30;`                                         | Identical syntax                                                  |
| **Update multiple columns**        | `UPDATE users SET age = 30, name = 'Rahim';`                        | `UPDATE users SET age = 30, name = 'Rahim';`                         | Identical syntax                                                  |
| **Update specific rows (with WHERE)** | `UPDATE users SET age = 30 WHERE id = 1;`                          | `UPDATE users SET age = 30 WHERE id = 1;`                            | Identical syntax                                                  |
| **Use expressions in update**      | `UPDATE users SET age = age + 1;`                                   | `UPDATE users SET age = age + 1;`                                    | Same behavior                                                     |
| **Update with JOIN**               | ```sql                                                              |
|                                   | UPDATE users                                                       |
|                                   | JOIN countries ON users.country_id = countries.id                  |
|                                   | SET users.country_name = countries.name;                           | ```sql                                                              |
|                                   | UPDATE users                                                       |
|                                   | SET country_name = c.name                                          |
|                                   | FROM countries c                                                   |
|                                   | WHERE users.country_id = c.id;                                     | PostgreSQL uses `FROM`, MySQL uses `JOIN` inside UPDATE             |
| **Update using subquery**          | `UPDATE users SET age = (SELECT MAX(age) FROM users);`              | Same as MySQL                                                       | Supported in both                                                 |
| **Update with LIMIT**              | `UPDATE users SET age = 30 LIMIT 10;`                               | Not supported directly                                               | Use CTE with `LIMIT` in PostgreSQL                                |
| **Update with ORDER BY + LIMIT**   | `UPDATE users SET age = 30 ORDER BY id DESC LIMIT 1;`               | Use CTE:<br>`WITH cte AS (SELECT id FROM users ORDER BY id DESC LIMIT 1) UPDATE users SET age = 30 WHERE id IN (SELECT id FROM cte);` | MySQL supports ORDER + LIMIT directly                             |
| **RETURNING clause**              | ❌ Not supported                                                     | `UPDATE users SET age = 30 RETURNING *;`                             | PostgreSQL supports `RETURNING` for fetching updated rows         |



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
### Constructing Relationship with Foreign Key
Lets having two table .user with attributes id,name and post with attribute id,post,user_id.post tables user_id attribute is a foreign key of user table.
so there might be co-relation between user tables id and post tables user_id.the id not exists in user table can't reference in post table.To ensure this validity REFERENCES key is used.

```
 create table user(
    id SERIAL PRIMARY KEY,
    name char(20)
 );

```CREATE TABLE post(
  id serial PRIMARY KEY,
   post TEXT,
   user_id INTEGER REFERENCES user(id)
);
```
### Enforcing Referential Integrity: Behaviors During Data Deletion
when user tables one data is deleted ,its corresponding post data can be handled.
3 ways
i) Restriction Deletion : on delete no action happen (default)
ii)Casecading Deletion : means all data of corresponding post table will also deleted ```ON DELETE CASCADE``` : 

```
```CREATE TABLE post(
  id serial PRIMARY KEY,
   post TEXT,
   user_id INTEGER REFERENCES user(id) ON DELETE CASCADE
);
```
lets say  ```DELETE user WHERE id=1;```
also delete all data of user_id=1 in post table 

iii)Setting Null: On delete corresponding value set null ```ON DELETE SET NULL```

```
```CREATE TABLE post(
  id serial PRIMARY KEY,
   post TEXT,
   user_id INTEGER REFERENCES user(id) ON DELETE SET NULL
);
```
lets say  ```DELETE user WHERE id=1;```
make user_id=NULL and all data remain as it is of user_id=1 in post table 



iv) setting default:  On delete corresponding value set default ```ON DELETE SET DEFAULT```


```
```CREATE TABLE post(
  id serial PRIMARY KEY,
   post TEXT,
   user_id INTEGER REFERENCES user(id) ON DELETE SET DEFAULT 2;
);
```
lets say  ```DELETE user WHERE id=1;```
make user_id=2 and all data remain as it is of user_id=1 in post table 

### JOIN
```select name,post from post JOIN user on user.id=post.user_id;```


