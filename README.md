
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


> ```CREATE USER IF NOT EXISTS adam@localhost IDENTIFIED BY 'jtp123456';  ```

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
- Insert Ignore statement in MySQL has a special feature that ignores the invalid rows whenever we are inserting single or multiple rows into a table. We can understand it with the following explanation, where a table contains a primary key column

- ``` INSERT IGNORE INTO table_name (column_names) VALUES ( value_list), ( value_list) .....; ```

##### Insert Into Select

- Sometimes we want to insert data of one table into the other table in the same or different database. It is not very easy to enter these data using the INSERT query manually. We can optimize this process with the use of MySQL INSERT INTO SELECT query. It allows us to populate the MySQL tables quickly. This section will cover the INSERT INTO SELECT command, syntax, and its use cases.
- ```INSERT INTO table_name (column_list) VALUES (value_list);   ```
- ```   INSERT INTO table_name2 SELECT * FROM table_name1 WHERE condition;   ```
- ``` INSERT INTO table2 TABLE table1; ```
- ``` INSERT INTO table_name2 (column_list)  SELECT column_list   FROM table_name1  WHERE condition;  ```

- ```Ex:- INSERT INTO person_info (person_name, email, city)  SELECT name, email, city  FROM person  WHERE city = 'Texas';   ```
 

## Mysql Indexes

- An index is a data structure that allows us to add indexes in the existing table. It enables you to improve the faster retrieval of records on a database table. It creates an entry for each value of the indexed columns. We use it to quickly find the record without searching each row in a database table whenever the table is accessed. We can create an index by using one or more columns of the table for efficient access to the records.

- When a table is created with a primary key or unique key, it automatically creates a special index named PRIMARY. We called this index as a clustered index. All indexes other than PRIMARY indexes are known as a non-clustered index or secondary index.

##### CREATE Index
- ``` CREATE INDEX [index_name] ON [table_name] (column names)   ```
- ``` CREATE INDEX ind_1 ON t_index(col4);   ```

> To see data in Details Way Use Explain Keyword Before query.
``` EXPLAIN SELECT studentid, firstname, lastname FROM student WHERE class = 'CS'; ```

##### DROP Index

- ```DROP INDEX index_name ON table_name [algorithm_option | lock_option];  ```
- ``` Algorithm [=] {DEFAULT | INPLACE | COPY}   ```
- COPY: This algorithm allows us to copy one table into another new table row by row and then DROP Index statement performed on this new table. On this table, we cannot perform an INSERT and UPDATE statement for data manipulation.

- INPLACE: This algorithm allows us to rebuild a table instead of copy the original table. We can perform all data manipulation operations on this table. On this table, MySQL issues an exclusive metadata lock during the index removal.
 


##### SHOW Index

- ``` SHOW INDEXES FROM table_name;   ```

> If we want to get the index information of a table in a different database or database to which you are not connected, MySQL allows us to specify the database name with the Show Indexes statement. The following statement explains it more clearly:

- ```mysql> SHOW INDEXES FROM table_name IN database_name;   ```
- ``` OR ```
- ``` SHOW INDEXES FROM database_name.table_name;   ```

##### UNIQUE Index
- ```CREATE UNIQUE INDEX index_name ON table_name (index_column1, index_column2,...); ```

##### CLUSTERED Index

- An index is a separate data structure that allows us to add indexes in the existing table. It enables you to improve the faster retrieval of records on a database table. It creates an entry for each value of the indexed columns.

- A clustered index is actually a table where the data for the rows are stored. It defines the order of the table data based on the key values that can be sorted in only one way. In the database, each table can have only one clustered index. In a relational database, if the table column contains a primary key or unique key, MySQL allows you to create a clustered index named PRIMARY based on that specific column.

- ``` CREATE TABLE `student_info` (  `studentid` int NOT NULL AUTO_INCREMENT,  `name` varchar(45) DEFAULT NULL,  `age` varchar(3) DEFAULT NULL,  `mobile` varchar(20) DEFAULT NULL,  `email` varchar(25) DEFAULT NULL,  PRIMARY KEY (`studentid`), //clustered index  UNIQUE KEY `email_UNIQUE` (`email`)) ```

## Mysql Clauses

##### WHERE KEYWORD
- MySQL WHERE Clause is used with SELECT, INSERT, UPDATE and DELETE clause to filter the results. It specifies a specific position where you have to do the operation.

- ```SELECT *  FROM officers  WHERE address = 'Mau';```
- ``` SELECT *  FROM officers  WHERE address = 'Lucknow'  AND officer_id < 5;   ```
- ```SELECT *  FROM officers  WHERE (address = 'Mau' AND officer_name = 'Ajeet')  OR (officer_id < 5); ```



##### DISTINCT KEYWORD
- MySQL DISTINCT clause is used to remove duplicate records from the table and fetch only the unique records. The DISTINCT clause is only used with the SELECT statement.
- ``` SELECT DISTINCT expressions  FROM tables  [WHERE conditions];   ```

##### FROM KEYWORD
- The MySQL FROM Clause is used to select some records from a table. It can also be used to retrieve records from multiple tables using JOIN condition.
- ``` FROM table1  [ { INNER JOIN | LEFT [OUTER] JOIN| RIGHT [OUTER] JOIN } table2  ON table1.column1 = table2.column1 ]   ``` 


##### ORDER BY KEYWORD

- The MYSQL ORDER BY Clause is used to sort the records in ascending or descending order.
- ``` SELECT expressions FROM tables  [WHERE conditions]  ORDER BY expression [ ASC | DESC ];   ```


##### GROUP BY KEYWORD

- The MYSQL GROUP BY Clause is used to collect data from multiple records and group the result by one or more column. It is generally used in a SELECT statement.

- You can also use some aggregate functions like COUNT, SUM, MIN, MAX, AVG etc. on the grouped column. 

- ``` SELECT expression1, expression2, ... expression_n,   aggregate_function (expression)  FROM tables  [WHERE conditions]  GROUP BY expression1, expression2, ... expression_n;   ```

- ``` SELECT emp_name, MIN/MAX/COUNT/AVG/SUM(working_hours) AS "Total working hours"  FROM employees  GROUP BY emp_name;   ```


##### HAVING
- MySQL HAVING Clause is used with GROUP BY clause. It always returns the rows where condition is TRUE.

-``` SELECT expression1, expression2, ... expression_n, aggregate_function (expression)  FROM tables  [WHERE conditions]  GROUP BY expression1, expression2, ... expression_n  HAVING condition;   ``` 

## Mysql Conditions

- AND
- OR
- AND OR 
- Boolean
- LIKE
- IN
- ANY
- Exists
- NOT
- Not Equal
- IS NULL
- IS NOT NULL
- BETWEEN

## Mysql JOIN
- MySQL JOINS are used with SELECT statement. It is used to retrieve data from multiple tables. It is performed whenever you need to fetch records from two or more tables.

##### JOIN
- MySQL JOINS are used with SELECT statement. It is used to retrieve data from multiple tables. It is performed whenever you need to fetch records from two or more tables.
- ``` SELECT columns  FROM table1   INNER JOIN table2  ON table1.column = table2.column;   ```


 ![INNER_JOIN_IMAGE](https://static.javatpoint.com/mysql/images/image1.png)

- ``` SELECT columns  FROM table1  LEFT [OUTER] JOIN table2  ON table1.column = table2.column;   ```


  ![LEFT_JOIN_IMAGE](https://static.javatpoint.com/mysql/images/image4.png)

- ``` SELECT columns  FROM table1  RIGHT [OUTER] JOIN table2  ON table1.column = table2.column;   ```


 ![RIGHT_JOIN_IMAGE](https://static.javatpoint.com/mysql/images/image7.png)



##### INNER JOIN
- The MySQL Inner Join is used to returns only those results from the tables that match the specified condition and hides other rows and columns. MySQL assumes it as a default Join, so it is optional to use the Inner Join keyword with the query.- 
- ``` SELECT columns  FROM table1   INNER JOIN table2  ON table1.column = table2.column;   ```


 ![INNER_JOIN_IMAGE](https://static.javatpoint.com/mysql/images/image1.png)



##### LEFT JOIN

- The Left Join in MySQL is used to query records from multiple tables. This clause is similar to the Inner Join clause that can be used with a SELECT statement immediately after the FROM keyword. When we use the Left Join clause, it will return all the records from the first (left-side) table, even no matching records found from the second (right side) table. If it will not find any matches record from the right side table, then returns null.

- In other words, the Left Join clause returns all the rows from the left table and matched records from the right table or returns Null if no matching record found. This Join can also be called a Left Outer Join clause. So, Outer is the optional keyword to use with Left Join.

- ``` SELECT columns  FROM table1  LEFT [OUTER] JOIN table2  ON table1.column = table2.column;   ```


  ![LEFT_JOIN_IMAGE](https://static.javatpoint.com/mysql/images/image4.png)

##### RIGHT JOIN

- The Right Join is used to joins two or more tables and returns all rows from the right-hand table, and only those results from the other table that fulfilled the join condition. If it finds unmatched records from the left side table, it returns Null value. It is similar to the Left Join, except it gives the reverse result of the join tables. It is also known as Right Outer Join. So, Outer is the optional clause used with the Right Join.
- ``` SELECT columns  FROM table1  RIGHT [OUTER] JOIN table2  ON table1.column = table2.column;   ```


 ![RIGHT_JOIN_IMAGE](https://static.javatpoint.com/mysql/images/image7.png)

##### CROSS JOIN
- MySQL CROSS JOIN is used to combine all possibilities of the two or more tables and returns the result that contains every row from all contributing tables. The CROSS JOIN is also known as CARTESIAN JOIN, which provides the Cartesian product of all associated tables. The Cartesian product can be explained as all rows present in the first table multiplied by all rows present in the second table. It is similar to the Inner Join, where the join condition is not available with this clause.


- ![CROSS_JOIN_IMAGE](https://static.javatpoint.com/mysql/images/mysql-cross-join.png) 


``` SELECT column-lists  FROM table1  CROSS JOIN table2;   ```


##### DELETE JOIN

- DELETE query is a sub-part of data manipulation language used for removing the rows from tables. How to delete join in MySQL is a very popular question during the interviews. It is not an easy process to use the delete join statements in MySQL. In this section, we are going to describe how you can delete records from multiple tables with the use of INNER JOIN or LEFT JOIN in the DELETE query.
- ``` DELETE target table   FROM    table1    INNER JOIN table2  ON table1.joining_column= table2.joining_column  WHERE   condition   ```

##### UPDATE JOIN

- UPDATE query in MySQL is a DML statement used for modifying the data of a table. The UPDATE query must require the SET and WHERE clause. The SET clause is used to change the values of the column specified in the WHERE clause.
``` UPDATE Tab1, Tab2, [INNER JOIN | LEFT JOIN] Tab1 ON Tab1.C1 = Tab2.C1  SET Tab1.C2 = Tab2.C2, Tab2.C3 = expression  WHERE Condition;   ```
