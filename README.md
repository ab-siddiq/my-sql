# MYSQL
# Table of contents
* [Create database](#create-database)
* [Make database default](#make-database-default)
* [Drop database](#drop-database)
* [Make database read only](#make-database-read-only)
* [Create table](#create-table)
* [Select table](#select-table)
* [Rename table](#rename-table)
* [Alter table](#alter-table)
* [Insert row](#insert-row)

## Create Database
 `CREATE DATABASE "databaseName";`

## Make database default
`USE "databaseName";`

## Drop database
`DROP DATABASE "databaseName";`

## Make database read only
`ALTER DATABASE "databaseName" READ ONLY = 1;`

NOTE: id the mode is readonly we can not drop the database. In order to drop the database we need to change the readonly mode by
`ALTER DATABASE "databaseName" READ ONLY = 0;`

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
## Select table
`SELECT * FROM "tableName";`
<br><br>
[Go Top](#my-sql)
## Rename table
`RENAME TABLE "name of the table" TO "new name of the table";`
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
