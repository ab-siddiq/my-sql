# Table of contents
* [Create table](#create-table)
## Create Database
 `CREATE DATABASE "databaseName";`

## Make Database Default
`USE "databaseName";`

## Drop Database
`DROP DATABASE "databaseName";`

## Make Database Readonly
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
```
