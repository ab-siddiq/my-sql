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


## Create Database
`CREATE DATABASE "databaseName";`
```mySQL
CREATE DATABASE employees;
```
## Make database default
`USE "databaseName";`
```mySQL
USE employees;
```
## Drop database
`DROP DATABASE "databaseName";`
```mySQL
DROP DATABASE employees;
```
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
<br><br>
[Go Top](#my-sql)
## Rename table
`RENAME TABLE "name of the table" TO "new name of the table";`
```mySQL
RENAME TABLE employees TO workers;
```
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
[Source of learning](https://www.youtube.com/watch?v=5OdVJbNCSso&ab_channel=BroCode)
