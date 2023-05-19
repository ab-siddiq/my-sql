# Table of contents
* [Create database](#create-database)
* [Make database default](#make-database-default)
* [Drop database](#drop-database)
* [Make database read only](#read-only)
* [Create table](#create-table)

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
```
