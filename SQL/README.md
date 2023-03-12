# Databases and SQL Tutorial

## Getting Started

#### 1. Databases
 - Data - raw information
 - Information - meaningful data

 - Database is a system which provides us some sort of usefull operations and it stores the data in a organised way
 - DBMS - It is a system which stores data and provide us a way of interatiion with that data

 - [Read more about databases](https://www.javatpoint.com/dbms-tutorial)

 #### 2. RDBMS
 - Data is stored in the form of rows and columns like tables, tables are also called as relations. 
 - MySQL and PostgreSQL are two popular RDBMS


 ## SQL(Structured Query Language)
  ### 1. Basics
  #### - Database Creation
  
  ```sql
    -- Syntax
    CREATE DATABASE <DATABASE_NAME>;
    -- Example:
    CREATE DATABASE Practice;

    -- Shell Output
    mysql> create database Practice;
    
    -- View exiting databases
    SHOW DATABASES;

    -- Shell Output
    mysql> show databases;
    +--------------------+
    | Database           |
    +--------------------+
    | dataanalytics      |
    | information_schema |
    | mysql              |
    | performance_schema |
    | practice           |
    | sys                |
    +--------------------+

    -- Use a particular database
    USE <DATABASE_NAME>;
   
    -- Shell Output
    mysql> use practice;
    Database changed
```
#### - Creating a new table
```sql
    -- Syntax
    CREATE TABLE <TABLE_NAME>(COLUMN1 DATA_TYPE,COLUMN2 DATA_TYPE, etc.);
    -- Example
    CREATE TABLE Students(student_id int, student_name varchar(20), student_age int);

    -- Shell Output
    mysql> create table Students(student_id int, student_name varchar(20), student_age int);
    Query OK, 0 rows affected (0.02 sec)

```
#### - Viewing & Deleting Tables
```sql    
    -- View all tables in current working database
    SHOW TABLES:
    
    -- Shell Output
    mysql> show tables;
    +--------------------+
    | Tables_in_practice |
    +--------------------+
    | students           |
    +--------------------+

    -- View table structure
    DESC <TABLE_NAME>;
    -- Example
    DESC Students;

    -- Shell Output
    mysql> desc students;
    +--------------+-------------+------+-----+---------+-------+
    | Field        | Type        | Null | Key | Default | Extra |
    +--------------+-------------+------+-----+---------+-------+
    | student_id   | int         | YES  |     | NULL    |       |
    | student_name | varchar(20) | YES  |     | NULL    |       |
    | student_age  | int         | YES  |     | NULL    |       |
    +--------------+-------------+------+-----+---------+-------+

    -- To delete a table
    -- Syntax
    DROP TABLE <TABLE_NAME>;

    -- Example
    DROP TABLE Students;
```

#### - Inserting data in tables
```sql
    -- Inserting data in tables
    -- Syntax
    -- When you want to insert data in all the columns of a table
    INSERT INTO <TABLE_NAME> VALUES(value1, value2, value3,....value n);
    -- or 
    -- When you want to insert data in selected columns of a table
    INSERT INTO <TABLE_NAME>(COLUMN_1, COLUMN_2,... etc.) VALUES(value1, value2, value3,....value n);

    -- Example
    INSERT INTO Students values(101,'Lovely',21);

    -- Shell Output
    mysql> insert into Students values(101,'Lovely',21);
    Query OK, 1 row affected (0.01 sec)
    --You can insert as many rows as you want 
    insert into Students values (102,'Jayesh',20);
    insert into Students values (103,'Noman',20);
```
#### - Viewing table data
```sql
    -- Now view the table data
    -- Syntax
    SELECT * FROM <TABLE_NAME>; -- This prints all the columns
    -- or
    SELECT <COLUMN_1,COLUMN_2, etc.> FROM <TABLE_NAME>; -- this prints only the specified columns

    -- Shell Output
    mysql> Select * from Students;
    +------------+--------------+-------------+
    | student_id | student_name | student_age |
    +------------+--------------+-------------+
    |        101 | Lovely       |          21 |
    |        102 | Jayesh       |          20 |
    |        103 | Noman        |          20 |
    +------------+--------------+-------------+    
  ```

#### - Updating table data
  ```sql
      -- To update a record in a table
      -- Syntax
      UPDATE <TABLE_NAME> SET <COLUMN_NAME> = <NEW_VALUE> WHERE <Condition>;
      -- the Where clause is used to specify a condition in order to target a single record, because if we don't specify the condition all the records will be updated instead of a single one.

      -- We can update multiple column in one go as well
      -- Syntax
      UPDATE <TABLE_NAME> SET <COLUMN1_NAME> = <NEW_VALUE>, <COLUMN2_NAME> = <NEW_VALUE>, <COLUMN n_NAME> = <NEW_VALUE> WHERE <Condition>;


      -- Example
      UPDATE Students SET student_age = 21 WHERE student_id = 102;
      -- Now this query will only update the student age column for a record where student id equals 102

      -- Shell output
      mysql> update Students set student_age = 21 where student_id = 102;
      Query OK, 1 row affected (0.01 sec)
      -- Run the SELECt * FROM Studensts; command in order to view the changes

  ```

#### - Deleting records in Table
```sql
    -- To delete a single records
    -- Syntax
    DELETE FROM <TABLE_NAME> WHERE <Condition>;
    -- The condition is an important factor over here so that you only end up deleting a specific row that you want
    
    -- Example
    DELETE FROM Students WHERE student_id = 103;
    -- It will only delete the record where the student id matches the value 103

    -- Delete all rows
    -- Syntax
    DELETE FROM <TABLE_NAME>;
    -- Since the condition factor is not specified all the rows will be deleted.(Risky)
```

  Types of commands in SQL - [Read more](https://www.javatpoint.com/dbms-sql-command)
  1. DDL (Data Definition Language) - these commands deal with the structure modification of table or columns.

    1. CREATE - To create tables

    2. ALTER - Further 4 types in ALTER command
      - ADD - adds the column
      - MODIFY - changes the column type
      - DROP - deletes column
      - CHANGE - change table name or column name
    
    3. DROP - To drop/delete tables

    4. Truncate -  To delete all rows from a table in one go
    
  2. DML (Data Manipulation Language) - these commands deal with the actual data that is stored inside of the tables.

    1. INSERT - To insert a new record in a table
    2. UPDATE - To update an existing record in a table.
    3. DELETE - To delete a record from a table.
    
  3. DCL (Data Control Language) - these commands control the data access.

    1. GRANT - To grant privileges such as data access, update, delete etc.
    2. REVOKE - To revoke access privileges.

  4. DQL (Data Query Language) - To read data.

    1. SELECT - To read table data

  5. TCL (Transaction Control Language) - Commands related to trasaction management.
  
    1. COMMIT - To permanently save the changes in the database
    2. ROLLBACK - To undo the changes made during the transaction.
    3. SAVEPOINT - To maintain a checkpoint in between the transaction.

