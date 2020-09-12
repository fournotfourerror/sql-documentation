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

#### DATA DEFINITION LANGUAGE (_DDL_)
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

#### DATA MANIPULATION LANGUAGE (_DML_)
The commands have ability to change the data inside the table called Data manipulation language commands.

The following are the commands for DML
 * INSERT
 
```sql
    INSERT INTO users VALUES('Hanuman','hanumankumar@gmail.com','M')
    
    INSERT INTO users(name, gender) VALUES('Kalyan','M')
```
 * DELETE
 
```sql
    DELETE FROM users WHERE email IS NULL;
    
    DELETE FROM users WHERE gender="F";
```

 * UPDATE
```sql
    UPDATE users SET name="Hanuman Kumar" WHERE name="Hanuman";
```
#### Data Control Language (_DCL_)
 * GRANT
   * Giving permissions to specific user(s)
 * REVOKE
   * Withdrawing the permissions which were given using `GRANT` command
   
#### Transaction Control Language (_TCL_)
 * COMMIT
 * ROLLBACK
 * SAVEPOINT
 
 #### Key constraints in SQL
 Key constraint is like a rule in Data Base Management System, that governs what kind of data should be inserted in a table
 
 * NOT NULL
  * The data shouldn't be a null value.
```sql
    CREATE TABLE workers (name varchar(20), email varchar(50) NOT NULL);
```
 
 * PRIMARY
   * The data shouldn't be a NULL and it should be a unique value.
   * A table should contain only one primary key
```sql
      CREATE TABLE persons(id int NOT NULL PRIMARY KEY, name varchar(20), salary int);
```
   * Auto increment with primary key
     * By using this we can insert data without mentioning it. And the data in the specific field will be incremented automatically by 1
     
```sql
     ALTER TABLE persons ADD id int PRIMARY KEY AUTO_INCREMENT;
```
 * FOREIGN
   * `FOREIGN KEY` is used to link two tables together
   * If a table contains `FOREIGN KEY`, it will be treated as a child table.
   * The field of table having `FOREIGN KEY` is refers to the `PRIMARY KEY` of another table
   
```sql
     CREATE TABLE persons_hike (id int, hike int, FOREIGN KEY(id) REFERRENCES persons(id) ON DELETE CASCADE)
```
 * UNIQUE
   * We've a limitation of using a primary key. i,e We can use only one primary key per a table. When we gonna use multiple primary keys, we will get errors because the primary rule for primary key is to maintain one primary key per table.
   * To overcome this disadvantage we can use another key constraint concept. i,e : `UNIQUE` key.
   * `UNIQUE` key is having same kind of rules as primary key have. But we can use multiple `UNIQUE KEYS` per a table.
   
```sql
    CREATE TABLE employees (emp_id int UNIQUE AUTO_INCREMENT, emp_name varchar(20),emp_email varchar(50) UNIQUE)
```

#### TASKS
 1. Create a table (sales) with the fields (emp_name,emp_job,emp_email,emp_salary). 
  * The emp_email Should be unique and should not allow the null values. 
  * Display the names of employees who are working as clerk, salesman or analyst and drawing a salary more than 3000.
  
```sql
    USE polytechnic;
    
    CREATE TABLE sales (emp_name varchar(20),emp_job varchar(20),emp_email varchar(50) PRIMARY    KEY,emp_salary int);
    
    // Inserting data
    USE polytechnic;
    INSERT INTO sales VALUES("John","clerk","john@gmail.com",5000);
    INSERT INTO sales VALUES("Jack","analyst","jack@gmail.com",2000);
    INSERT INTO sales VALUES("Tom","salesman","tom@gmail.com",3000);
    INSERT INTO sales VALUES("Smith","clerk","smith@gmail.com",3500);
    INSERT INTO sales VALUES("Ninad","salesman","ninad@gmail.com",2600);
    
    
    USE polytechnic;
    SELECT emp_name FROM sales WHERE(emp_job="salesman" or emp_job="clerk" or emp_job="analyst") and emp_salary>3000;
    
    USE polytechnic;
    SELECT emp_name FROM sales WHERE emp_job in('clerk','salesman','analyst') and emp_salary>3000;
```

#### Wildcards
We have to use the concept of `wildcards` for implementing pattern matching functionality. We can implement this by using `LIKE` keyword.

* **%** => It takes multiple characters for pattern matching
 * a% => The data must and should starts with the character `a`
 * %a => The data must and should ends with the character `a`
 * %a% => The data must and should contains the character of `a` in it.
 
```sql
   SELECT * FROM users WHERE name LIKE "a%";
   
   SELECT * FROM users WHERE name LIKE "%a"
   
   SELECT * FROM users WHERE name LIKE "%a%"
```

* Underscore (`_`)
  This wildcard is used for matching a specific range of characters.
  * _ => Matching with single character
  * _ _ => Matching with two characters

```sql
   // The data which we are going to select must and should have the character a in second position
   SELECT * FROM users WHERE name LIKE "_a%";
   
   // The data which we are gonna retrive should contain 6 characters long and should contain H as the first character.
   SELECT * FROM users WHERE name LIKE "H_ _ _ _ _"
   
   // The data which we are gonna select should have atleast 6 characters long.
   SELECT * FROM users WHERE name LIKE "H_ _ _ _ _ %"
  
```
#### Relationships
* One-to-one
* One-to-many
* Many-to-many

#### Joins
A join is used to combine multiple tables together. By using this we can combine the data exists in rows of the tables.

* INNER JOIN

```sql
    SELECT student_info.student_id, student_info.name, certifications.certification FROM certifications INNER JOIN student_info ON student_info.student_id=certifications.student_id;
```

* LEFT JOIN

```sql
    SELECT student_info.student_id,student_info.name,certifications.certification FROM student_info LEFT JOIN certifications ON student_info.student_id=certifications.student_id
```

* RIGHT JOIN

```sql
    SELECT student_info.student_id, student_info.name, certifications.certification FROM student_info RIGHT JOIN certifications ON student_info.student_id=certifications.student_id

```
* FULL JOIN
```sql
    SELECT * FROM student_info LEFT JOIN certifications ON student_info.student_id=certifications.student_id UNION SELECT * FROM student_info RIGHT JOIN certifications ON student_info.student_id=certifications.student_id
```
