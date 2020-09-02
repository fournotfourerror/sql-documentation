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
```
