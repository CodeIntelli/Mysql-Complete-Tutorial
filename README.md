
# Mysql-Complete-Tutorial

![MySql_Logo](https://res.cloudinary.com/dgxjx6rwm/image/upload/v1646374316/Github/Mysql_xpc3pk.gif)

MySQL is a relational database management system based on the Structured Query Language, which is the popular language for accessing and managing the records in the database. MySQL is open-source and free software under the GNU license. It is supported by Oracle Company.

# Mysql Tutorial

## Users Query

##### Show Users/List All Users

- ```select user from mysql.user``` 

    > Note: If we want to see more information on the user table, execute the command below:
    ``` DESC user;```
    > To get the selected information like as hostname, password expiration status, and account locking, execute the query as below:
    ```SELECT user, host, account_locked, password_expired FROM user;``` 

##### Show Current User

- ```Select current_user();```

##### Insert User 
- ```create user sam@localhost identified by 'jtp12345'```  

> Note:- Now, we will use the IF NOT EXISTS clause with the CREATE USER statement. 
```CREATE USER IF NOT EXISTS adam@localhost IDENTIFIED BY 'jtp123456';  ```

##### Drop Users

- ```DROP USER shiva@localhost;```  

> Note: The DROP USER statement can also be used to remove more than one user accounts at once. We can drop multiple user accounts by separating account_name with comma operator. To delete multiple user accounts, execute the following command.
```DROP USER ram@localhost, sam@localhost```

##### Change Mysql User Password

 - ```UPDATE user SET password = PASSWORD('jtp12345') WHERE user = 'peter' AND host = 'localhost'; ```


## Grant Privileges to the MySQL New User
MySQL server provides multiple types of privileges to a new user account. Some of the most commonly used privileges are given below:

- **ALL PRIVILEGES:** It permits all privileges to a new user account.
- **CREATE:** It enables the user account to create databases and tables.
- **DROP:** It enables the user account to drop databases and tables.
- **DELETE:** It enables the user account to delete rows from a specific table.
- **INSERT:** It enables the user account to insert rows into a specific table.
- **SELECT:** It enables the user account to read a database.
- **UPDATE:** It enables the user account to update table rows.

- If you want to give all privileges to a newly created user, execute the following command.
    ```GRANT ALL PRIVILEGES ON * . * TO peter@localhost; ```

- If you want to give specific privileges to a newly created user, execute the following command.
    ```GRANT CREATE, SELECT, INSERT ON * . * TO peter@localhost;```  

- Sometimes, you want to flush all the privileges of a user account for changes occurs immediately, type the following command.
    ```FLUSH PRIVILEGES;```  

- If you want to see the existing privileges for the user, execute the following command.
    ```SHOW GRANTS for username;```  

## Table Query

##### Create Table

- ```CREATE TABLE employee_table(id int NOT NULL AUTO_INCREMENT,name varchar(45) NOT NULL, occupation varchar(35) NOT NULL, age int NOT NULL,PRIMARY KEY (id));```  

##### Alter Table

Add a column in a table after inserting

- ```ALTER TABLE table_name ADD new_column_name column_definition [ FIRST | AFTER column_name ];```
 

- ```ALTER TABLE cus_tbl ADD cus_age varchar(40) NOT NULL; ```

Add Multiple Columns

- ``` ALTER TABLE table_name ADD new_column_name column_definition [ FIRST | AFTER column_name ], ADD new_column_name column_definition [ FIRST | AFTER column_name ];```

- ```ALTER TABLE cus_tbl ADD cus_address varchar(100) NOT NULL AFTER cus_surname,ADD cus_salary int(100) NOT NULL AFTER cus_age ;```


MODIFY column in the table

> ```ALTER TABLE table_nameMODIFY column_name column_definition [ FIRST | AFTER column_name ];```  

- ```ALTER TABLE cus_tbl MODIFY cus_surname varchar(50) NULL;```


 DROP column in table

> ```ALTER TABLE table_name DROP COLUMN column_name;```  

- ``` ALTER TABLE cus_tbl DROP COLUMN cus_address;   ```

RENAME column in table

> ``` ALTER TABLE table_name CHANGE COLUMN old_name new_name column_definition [ FIRST | AFTER column_name ]  ```

- ```  ALTER TABLE  cus_tbl CHANGE COLUMN cus_surname cus_title varchar(20) NOT NULL;  ```

RENAME table

> ``` ALTER TABLE table_name RENAME TO new_table_name;  ```

- ``` ALTER TABLE cus_tbl RENAME TO cus_table;  ```

##### Show Table
-    ```mysql> SHOW TABLES FROM mystudentdb;```  
                    ```OR,```
    ```mysql> SHOW TABLES IN mystudentdb; ```

##### Rename Table

- ```RENAME old_table TO new_table; ``` 

##### Truncate Table


- ```TRUNCATE TABLE table_name1;   ```
 

##### Add/Delete Column

- ``` ALTER TABLE Test ADD COLUMN City VARCHAR(30) NOT NULL;   ```

- ```ALTER TABLE table_name  DROP COLUMN column_name; ```


##### Show Columns

- ```SHOW COLUMNS FROM student_info;```
- ```SHOW FULL COLUMNS FROM student_info;``` 
- ```SHOW COLUMNS FROM student_info LIKE 's%';```


##### Rename Columns

- ```ALTER TABLE table_name CHANGE COLUMN old_column_name new_column_name Data Type;```

> Multiple Table 
- ```ALTER TABLE table_name CHANGE old_column_name1 new_column_name1 Data Type, CHANGE old_column_name2 new_column_name2 Data Type, CHANGE old_column_nameN new_column_nameN Data Type;  ```

##### Table Locking

- ``` LOCK TABLES tab_name1 [READ | WRITE], tab_name2 [READ | WRITE],...... ;  ```

##### Account Lock

- ```CREATE USER account_name IDENTIFIED BY 'password' ACCOUNT LOCK;```

##### Account Unlock

-  ```ALTER USER [IF EXISTS] user_account_name ACCOUNT UNLOCK;  ```

## Record Queries

##### Constraints

- The constraint in MySQL is used to specify the rule that allows or restricts what values/data will be stored in the table. They provide a suitable method to ensure data accuracy and integrity inside the table. It also helps to limit the type of data that will be inserted inside the table. If any interruption occurs between the constraint and data action, the action is failed.

- Constraints used in MySQL
The following are the most common constraints used in the MySQL:

    - NOT NULL.
        - ```CREATE TABLE Student(Id INTEGER, LastName TEXT NOT NULL, FirstName TEXT NOT NULL, City VARCHAR(35));   ```
    - CHECK
    
        - ```[CONSTRAINT [symbol]] CHECK (expr) [[NOT] ENFORCED]  ```
        - ``` CREATE TABLE Persons (ID int NOT NULL,Name varchar(45) NOT NULL, Age int CHECK (Age>=18));  ```
        
    - DEFAULT
        - ```CREATE TABLE Persons ( ID int NOT NULL, Name varchar(45) NOT NULL, Age int, City varchar(25) DEFAULT 'New York');``` 
    - PRIMARY KEY
        - ```CREATE TABLE Persons (ID int NOT NULL PRIMARY KEY, Name varchar(45) NOT NULL,Age int,City varchar(25)); ```
    - AUTO_INCREMENT
        - ``` CREATE TABLE Animals(id int NOT NULL AUTO_INCREMENT,name CHAR(30) NOT NULL,PRIMARY KEY (id)) ```
    - UNIQUE
        - ```CREATE TABLE ShirtBrands(Id INTEGER, BrandName VARCHAR(40) UNIQUE, Size VARCHAR(30)); ```
    - INDEX
        - ``` CREATE TABLE Persons (Person_ID int NOT NULL PRIMARY KEY, Name varchar(45) NOT NULL, Age int,City varchar(25));   ```
    - ENUM
        - ``` CREATE TABLE Shirts (id INT PRIMARY KEY AUTO_INCREMENT,name VARCHAR(35),size ENUM('small', 'medium', 'large', 'x-large'));   ```
    - FOREIGN KEY 
        - ``` CREATE TABLE Shirts (id INT PRIMARY KEY AUTO_INCREMENT, name VARCHAR(35), size ENUM('small', 'medium', 'large', 'x-large'));   ```



##### INSERT Records

- ``` INSERT INTO People (id, name, occupation, age) VALUES (101, 'Peter', 'Engineer', 32);```
    
- ``` INSERT INTO table_name (column_name, column_date) VALUES ('DATE: Manual Date', '2008-7-04');   ```
    
##### UPDATE Record
    
- ``` UPDATE table_name SET column_name1 = new-value1, column_name2=new-value2, [WHERE Clause] ```

##### DELETE Record

- ```DELETE FROM Employees ORDER BY name LIMIT 3;   ```
> For example, the following query first sorts the employees according to their names alphabetically and deletes the first three employees from the table



##### SELECT Record

- ``` SELECT field_name1, field_name 2,... field_nameN FROM table_name1, table_name2... [WHERE condition] [GROUP BY field_name(s)] [HAVING condition] [ORDER BY field_name(s)] [OFFSET M ][LIMIT N];```

| Plugin | README |
| ------ | ------ |
| field_name(s) or * | It is used to specify one or more columns to returns in the result set. The asterisk (*) returns all fields of a table. |
| table_name(s) | 	It is the name of tables from which we want to fetch data. |
| WHERE | It is an optional clause. It specifies the condition that returned the matched records in the result set. |
| GROUP BY | It is optional. It collects data from multiple records and grouped them by one or more columns. |
| HAVING | It is optional. It works with the GROUP BY clause and returns only those rows whose condition is TRUE.|
| ORDER BY | It is optional. It is used for sorting the records in the result set. |
| OFFSET | It is optional. It specifies to which row returns first. By default, It starts with zero. |
| LIMIT | It is optional. It is used to limit the number of returned records in the result set. |

##### REPLACE Record
- The REPLACE statement in MySQL is an extension of the SQL Standard. This statement works the same as the INSERT statement, except that if an old row matches the new record in the table for a PRIMARY KEY or a UNIQUE index, this command deleted the old row before the new row is added.
- ``` REPLACE [INTO] table_name(column_list) VALUES(value_list);   ``` 
- ```REPLACE INTO table SET column1 = value1, column2 = value2;  ```





##### INSERT IGNORE
##### Insert Into Select

## Mysql Indexes


##### CREATE Index
##### DROP Index
##### SHOW Index
##### UNIQUE Index
##### CLUSTERED Index

## Mysql Clauses

##### WHERE KEYWORD
##### DISTINCT KEYWORD
##### FROM KEYWORD
##### ORDER BY KEYWORD
##### GROUP BY KEYWORD
##### HAVING

## Mysql Conditions

##### AND
##### OR
##### AND OR 
##### Boolean
##### LIKE
##### IN
##### ANY
##### Exists
##### NOT
##### Not Equal
##### IS NULL
##### IS NOT NULL
##### BETWEEN

## Mysql JOIN


##### JOIN
##### INNER JOIN
##### LEFT JOIN
##### RIGHT JOIN
##### CROSS JOIN
##### SELF JOIN
##### DELETE JOIN
##### UPDATE JOIN
##### EQUAL JOIN
##### NATURAL JOIN


















