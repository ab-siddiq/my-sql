# MYSQL
# Table of contents
* [Create database](#create-database)
* [Make database default](#make-database-default)
* [Drop database](#drop-database)
* [Make database read only](#make-database-read-only)
* [Create table](#create-table)
* [Insert row](#insert-row)
* [Select table](#select-table)
* [Rename table](#rename-table)
* [Alter table](#alter-table)
* [Update table](#update-table)
* [Delete table](#delete-table)
* [Auto commit](#auto-commit)
* [Commit](#commit)
* [Roll back](#roll-back)
* [Current date, time](#current-date-time)
* [Unique](#unique)
* [Not null](#not-null)
* [Check](#check)
* [Default](#default)


## Create Database
`CREATE DATABASE "databaseName";`
```mySQL
CREATE DATABASE employees;
```
[Jump To Top &#8593;](#mysql)<br>
## Make database default
`USE "databaseName";`
```mySQL
USE employees;
```
[Jump To Top &#8593;](#mysql)<br>
## Drop database
`DROP DATABASE "databaseName";`
```mySQL
DROP DATABASE employees;
```
[Jump To Top &#8593;](#mysql)<br>
## Make database read only
`ALTER DATABASE "databaseName" READ ONLY = 1;`
```mySQL
ALTER DATABASE employees READ ONLY = 1;
```
NOTE: id the mode is readonly we can not drop the database. In order to drop the database we need to change the readonly mode by
`ALTER DATABASE "databaseName" READ ONLY = 0;`
```mySQL
ALTER DATABASE employees READ ONLY = 0;
```
[Jump To Top &#8593;](#mysql)<br>
## Create table
Example  `CREATE TABLE "tableName" (column name comma separeted)`
```mySQL
CREATE TABLE employees(
  employee_id INT,
  first_name VARCHAR(50),
  last_name VARCHAR(50),
  hourly_pay DECIMAL(5,2),
  hire_date DATE
)
//Here "hourly_pay DECIMAL(5,2)" 5,2 is the number of decimal digits with 2 decimal point.  for example - 123.23
```
[Jump To Top &#8593;](#mysql)<br>
# Insert row
To insert row we need to add values sequencially one after another following the data types
```mySQL
INSERT INTO employees
VALUES(1,"Md. Ariful","Haque","arif@sebpo.com",400.00,"2020-03-04");
```
To insert multiple row
```mySQL
INSERT INTO employees
VALUES(1,"Md. Ariful","Haque","arif@sebpo.com",400.00,"2020-03-04"),
      (2,"Md. Abir","Hossain","abir@sebpo.com",400.00,"2020-03-04"),
      (3,"Md. Abdur","Rahman","abdur@sebpo.com",400.00,"2020-03-04") ;
```
To insert 1 or 2 data we need to specify the column name within first bracket after table name
```mySQL
INSERT INTO employees (employee_id,first_name,last_name)
VALUES(5,"Md. Sabbir","Hossain");
```
[Jump To Top &#8593;](#mysql)<br>
## Select table
To get all the column
`SELECT * FROM "tableName";`
```mySQL
SELECT * FROM employees;
```
To get 1 or n column
`SELECT column name comma separated FROM "tableName";`
```mySQL
SELECT employee_id, first_name, last_name FROM employees;
```
To get specific column with matching data
```mySQL
SELECT * FROM employees
WHERE hourly_pay = 200.00;
```
```mySQL
SELECT * FROM employees
WHERE hourly_pay >= 200.00;
```
```mySQL
SELECT * FROM employees
WHERE hourly_pay != 200.00;
```
```mySQL
SELECT * FROM employees
WHERE hourly_pay IS NULL;
```
```mySQL
SELECT * FROM employees
WHERE hourly_pay IS NOT NULL;
```
[Jump To Top &#8593;](#mysql)<br>
## Rename table
`RENAME TABLE "name of the table" TO "new name of the table";`
```mySQL
RENAME TABLE employees TO workers;
```
[Jump To Top &#8593;](#mysql)<br>
## Alter table
To add new column 
```mySQL
ALTER TABLE employees
ADD phone_number VARCHAR(15);
```
To rename column
```mySQL
ALTER TABLE employees
RENAME COLUMN phone_number TO enail;
```
To modify table column 
```mySQL
ALTER TABLE employees
MODIFY COLUMN email VARCHAR(100);
```
To move the column position 
```mySQL
ALTER TABLE employees
MODIFY email VARCHAR(100)
AFTER last_name;
```
Delete column from table
```mySQL
ALTER TABLE employees
DROP COLUMN email;
```
Move column position to first 
```mySQL
ALTER TABLE employees
MODIFY email VARCHAR(100)
FIRST;
```
[Jump To Top &#8593;](#mysql)<br>
## Update table
`UPDATE` "table name";
To update table we can update one or more elements. If want to update more than one element than need to write using comma. And also need specify which one we want to update.
```mySQL
UPDATE employees
SET joining_date="2023-05-12",email="ayan@sebpo.com",salary=25000.00
WHERE employee_id=5;
```
If we want to set the value to null than just need to set the value equals null
```mySQL
UPDATE employees
SET joining_date=NULL
WHERE employee_id=5;
```
To update all of the row we need to skip the `WHERE` clouse. All of the column of  `joining_date` will be updated by the following query.
```mySQL
UPDATE employees
SET joining_date="2023-05-12";
```
[Jump To Top &#8593;](#mysql)<br>
## Delete table 
`DELETE FROM` "table name";
If we want to delete the whole table row we need to just write the following query and it will delete everything from the table.
```mySQL
DELETE FROM employees;
```
To avoid deleting everything we need to follow the below query. It will delete only the row which is sepecified under the `WHERE` clouse
```mySQL
DELETE FROM employees
WHERE employee_id=5;
```
[Jump To Top &#8593;](#mysql)<br>
## Auto commit
Suppose we are going to delete one row from our table and by mistake we forgot to add the `WHERE` clouse. Then what happen? All the row from the table table will vanish. To get rid from this situation we need to create a safe mode by adding the below query
```mySQL
SET AUTOCOMMIT = OFF;
```
[Jump To Top &#8593;](#mysql)<br>
## Commit
When we create a safe mode by adding `AUTO COMMIT = OFF` then we need to manually commit by `COMMIT` clouse. After `AUTO COMMIT = OFF`<br> Note: we must run the query `COMMIt` `otherwise it will not restore the table data`.
```mySQL
COMMIT;
```
[Jump To Top &#8593;](#mysql)<br>
## Roll back
When we create a safe mode and delete all the row from table by mistake we can restore them by `ROLLABACK` clouse
```mySQL
ROLLBACK;
```
## Current date, time
For current date the data type is `DATE`, current time datat type is `TIME`, current date time data type is `DATETIME`
```mySQL
CREATE TABLE date_time(
c_date DATE,
c_time TIME,
current_date_time DATETIME
);
```
To insert current date, date or date time we have `CURRENT_DATE()`, `CURRENT_TIME()`, `NOW()` function
```mySQL
INSERT INTO date_time
VALUES (CURRENT_DATE(),CURRENT_TIME(),NOW());
```
We can add also the previous or the next date or time by adding decimal values
```mySQL
INSERT INTO date_time
VALUES (CURRENT_DATE()-1,CURRENT_TIME(),NOW());
```
If we want to add NULL value we just put null
```mySQL
INSERT INTO date_time
VALUES (null,NULL,NULL);
```
[Jump To Top &#8593;](#mysql)<br>
# Unique
```MYsql
CREATE TABLE products(
product_id INT,
product_name VARCHAR(50) UNIQUE,
product_price DECIMAL(10,2)
)
```
In case if you forgot to set `UNIQUE` identifier you can set it later by the following query
```mySQL
ALTER TABLE products
ADD CONSTRAINT
UNIQUE(product_id);
```
[Jump To Top &#8593;](#mysql)<br>
# Not null
When creating a table you can set a specific column that value must be filled by the following query
```mySQL
CREATE TABLE products(
product_id INT,
product_name VARCHAR(50) NOT NULL,
product_price DECIMAL(10,2)
);
```
If you forgot to set no null you can add that later by following the below
```mySQL
ALTER TABLE products
MODIFY product_name varchar(20) NOT NULL;
```
[Jump To Top &#8593;](#mysql)<br>
# Check
```mySQL
CREATE TABLE employees(
  employee_id INT,
  first_name VARCHAR(50),
  last_name VARCHAR(50),
  salary DECIMAL(8,2),
  hire_date DATE,
  CHECK(salary=>15000)
)

or
CREATE TABLE employees(
  employee_id INT,
  first_name VARCHAR(50),
  last_name VARCHAR(50),
  salary DECIMAL(8,2),
  hire_date DATE,
  CONTRAINT check_salary CHECK(salary=>15000)
)
```
Add checck to existing table
```mySQL
ALTER TABLE employees
ADD CHECK(salary>=15000);

or
ALTER TABLE employees
ADD CONSTRAINT check_salary CHECK(salary>=15000);
```
Delete check
```mySQL
ALTER TABLE employees
DROP CHECK check_salary;
```
[Jump To Top &#8593;](#mysql)<br>
# Default
To set default value in a new table
```mySQL
CREATE TABLE employees(
  employee_id INT,
  first_name VARCHAR(50),
  last_name VARCHAR(50),
  salary DECIMAL(8,2) DEFAULT 0,
  hire_date DATE,
)
```
To set default value in an existing table
```mySQL
ALTER TABLE employee
ALTER salary SET DEFAULT 0;
```
[Jump To Top &#8593;](#mysql)<br>
[Jump To Top &#8593;](#mysql)<br>
[Jump To Top &#8593;](#mysql)<br>
[Jump To Top &#8593;](#mysql)<br>
[Jump To Top &#8593;](#mysql)<br>
[Jump To Top &#8593;](#mysql)<br>
[Jump To Top &#8593;](#mysql)<br>
[Jump To Top &#8593;](#mysql)<br>
[Source of learning](https://www.youtube.com/watch?v=5OdVJbNCSso&ab_channel=BroCode)

