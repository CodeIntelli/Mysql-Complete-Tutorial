
# Mysql-Complete-Tutorial

![MySql_Logo](https://res.cloudinary.com/dgxjx6rwm/image/upload/v1646374316/Github/Mysql_xpc3pk.gif)

MySQL is a relational database management system based on the Structured Query Language, which is the popular language for accessing and managing the records in the database. MySQL is open-source and free software under the GNU license. It is supported by Oracle Company.


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
##### Alter Table
##### Show Table
##### Rename Table
##### Truncate Table
##### Describe Table
##### Drop Table
##### Temporary Table
##### Copy Table
##### Repair Table
##### Add/Delete Column
##### Show Columns
##### Rename Columns
##### Views
##### Table Locking
##### Account Lock
##### Account Unlock


## Record Queries

##### Constraints
##### INSERT Records
##### UPDATE Record
##### DELETE Record
##### SELECT Record
##### REPLACE Record
##### Insert On Duplicate Key Update
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


















