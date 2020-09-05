# sql-documentation

### Data base:  `A storage area to store Collection of information`
* FMS (File management system)
  * AFMS is a type of software that manages data files in a computer system. It has limited capabilities and designed to manage individual or group of files.
  
  * Advantages:
    * The performance is very high
    * It is easy to maintain
    
  * Limitations
    * It has low security
    
* DBMS or RDBMS
  * Database management system is a software for storing and retrieving user's information while considering appropriate security measures. And it follows a structure to store the information. We've to follow a language for communicating with it such as sql (Structured query language)
  * Advantages
    * It maintains security
    * Stores information in structured order
    
  * Limitations
    * The performance is very slow
    * Somewhat complex to maintain
    
  * Examples:
    * Oracle
    * mySql
    
* Nosql (Not only sql)
  ` FMS + DBMS `
  The combination of security and the performance.
  * Examples:
    * Mongo
    * Firebase
    
 **CREATING A DATABASE**
 ```sql
     CREATE DATABASE <db_name>;
 ```
 
 Example
 ```sql
    CREATE DATABASE 'employees'
 ```
 
**DROPING A DATABASE**
```sql
   DROP DATABASE <db_name>
```

Example

```sql
    DROP DATABASE 'employees'
```

**SELECTING A DATABASE**
```sql
    USE <db_name>
```

Example
```sql
    USE 'employees'
```

**CHECKING HOW MANY TABLE AVAILABLE IN DATABASE**
```sql
    USE 'employees';
    SHOW TABLES;
```

#### DATA TYPES
```sql
    varchar   (// Varchar takes empty values) (0-255)
    varchar2  (// It doesn't allow empty values or null values) (0-255)
    int       (// For numerical values) (-2147483648 to 2147483647)
    float     (// Decimal values) ( Upto 23 digits)
    char      (// For representing text) (0-255)
    BLOB      (// Large amount data (Images)) (0-65535) BLOB - Binary Large OBject
    LONGBLOB  (// For storing large objects) (0-4294967295)
    MEDIUMBLOB(// For storing medium sized objects) (0-16777215)
    CLOB      (// For storing videos)
    text      (// For storing text) (0-65535)
```

**CREATING TABLE**
```sql
    USE employees;
    CREATE TABLE 'users' (name varchar(30),email varchar(100), gender char(1));
```

**INSERTING DATA INTO TABLE**
```sql
    INSERT INTO users VALUES('Hanuman','hanumankumar@gmail.com','M')
    
    INSERT INTO users(name, gender) VALUES('Kalyan','M')
```

**RETRIEVING DATA FROM TABLE**

```sql
    SELECT * FROM <table_name>
    
    SELECT * FROM users
    
    SELECT name FROM users
    
    SELECT email FROM users
```

**WHERE Clause**

By using `WHERE` clause we can retrieve data based on a condition

Example

```sql
      SELECT * FROM users WHERE name='Hanuman';
      
      SELECT email FROM users WHERE name='Hanuman';
```

**DISTINCT**

By using this keyword we can reduce the data redundancy while retrieving information from tables.

```sql
    SELECT DISTINCT name FROM users
```

**Operators in SQL**
* Arithmatic operators (+,-,*,/,%)
```sql
    SELECT 30+5
```

* Logical
  Logical operators are used for conditional retrieving of the data

 * AND
 * OR
 * NOT
 * ANY
 
 ```sql
     SELECT * FROM users WHERE name='Hanuman' AND email='hanumanhkumar@gmail.com';
     
     SELECT * FROM users WHERE name='Hanuman' OR email='hanumankumar@gmail.com';
     
     SELECT * FROM users WHERE NOT name='Hanuman';
     
     SELECT * FROM users WHERE email=ANY(SELECT email FROM users WHERE email='hanumankumar@gmail.com')
     
     SELECT name FROM users WHERE gender=ANY(SELECT gender FROM users WHERE email='hanumankumar@gmail.com')
 ```
* Comparision operators
 * =, !=, <>, < ,>,<=, >=
 
* Aggrigation:
  Returning a single value based on multiple value in a field.
  * MAX()
  * MIN()
  * AVG()
  * SUM()
  * COUNT()
    
    * COUNT(*)

        This is for checking no.of rows avaulable in the table.
  
        Example 
  
  ```sql
         SELECT COUNT(*) FROM users;
  ```
  
     * COUNT(_filed_name_)

       This is for counting number of rows available in a specific field. It counts all the data excepts the empty or NULL values.
  
  ```sql
        SELECT COUNT(email) FROM users;
  ```

**FINDING 2nd LARGEST SALARY**
```sql
     SELECT MAX(salary) FROM workers WHERE salary < (SELECT MAX(salary) FROM workers)
```
**FINDING 3rd LARGEST SALARY**

```sql
    SELECT MAX(salary) FROM workers WHERE salary<(SELECT MAX(salary) FROM workers WHERE salary < (SELECT MAX(salary) FROM workers))
```

#### DATA DEFINITION LANGUAGE
This language consists of various keywords. These are used to manipulate the structure of a table. When we're gonna apply the commands, the structure of table will be changed.

* CREATE
* DROP
```sql
     DROP TABLE employees
```
* ALTER
```sql
     //Adding a new column
     ALTER TABLE workers ADD dob varchar(30)
     
     // Here ADD is the keyword to add a new column and dob is the column name
     
     //Changing the column name of a table(workers)
     ALTER TABLE workers CHANGE dob Date_of_birth varchar(30)
     
     //Dropping a column from a table
     ALTER TABLE workers DROP COLUMN Date_of_birth;
```
* TRUNCATE
