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
