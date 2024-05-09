# SQL - Structured Query Language Notes
### To execute a command on MySQL Workbench click the button of the thunder bold with a capital "I", then in the lefthand column look under the tab named "Schemas" and click the arrow dropdown of the respective tab inside of your database.
***
#### What command do you use to create a database?
```sql
CREATE DATABASE record_company;
```
You input the above command and give the database a name followed by a semicolon.
***
#### What is the command to use that database?
```sql
USE record_company;
```
You input the above command to use the database and whatever the name is that you're calling your database followed by a semicolon.
***
#### A. What command do you use to create a table in the database?
```sql
CREATE TABLE test
```
You input the above command and give the table a name without a semicolon.
***
#### B. What command do you use to create a column inside of the table?
```sql
CREATE TABLE test (
  test_column INT
);
```
You input the above command and give the column a name followed by the property type of the data it will contain, in this case an integer, without a semicolon - if you append it with a semicolon it will give an error. 
***
#### A. What command do you use to precede the step of adding another column to the table after you already created it? 
```sql
ALTER TABLE test
```
You input the above command and specify the table (inside which you want to add a new column).
***
#### B. What command do you use to actually add a new column inside the table, that is, tell it what you want to do?
```sql
ADD another_column VARCHAR(255);
```
You input the above command and give the new column a name and specify the property of the data it will contain, in this case a string, followed by the a semicolon. `VARCHAR(255)` is the easiest way to input the string datatype, it stands for variable length character array, and the maximum length that you want it to be is 255 characters. 
***
#### What command do you use to remove a table from the database?
```sql
DROP TABLE test;
```
You input the above command it will completely remove the table from the database in the schema of the record company. 
***
Delete all but the remaining code below
```sql
CREATE DATABASE record_company;
USE record_company;
```
Now we want to add a table to hold all the bands that are part of our record company.
***
#### What is the command to add a new table named `band` to the database?
```sql
CREATE DATABASE record_company;
USE record_company;
CREATE TABLE bands (
  name VARCHAR(255) NOT NULL
);
```
You input the above command to create a new table called `bands` that will hold the name of a band that is a string datatype and `NOT NULL` which means that `bands` cannot be entered unless it has a name to force the table to have values that are defined otherwise it will force an error.
***
#### What is the command to add an ID column to our table?
```sql
CREATE DATABASE record_company;
USE record_company;
CREATE TABLE bands (
  id INT NOT NULL AUTO_INCREMENT,
  name VARCHAR(255) NOT NULL
);
```
You input the above command to add an `id` column, `INT` which means that it will be an integer, `NOT NULL` again forcing the table to have values that defined, and `AUTO_INCREMENT` which means that it automatically generates ids incremented for each successive band; lastly, we add a coma so that SQL knows that the above commands represent two different columns. This is useful because it will help distinguish between `bands` which may contain the same name by uniquely defining the row from all the other rows in that column.
***
#### What is the command to tell SQL that `id` is the primary column inside of our `bands` table in our `record_company` file?
```sql
CREATE DATABASE record_company;
USE record_company;
CREATE TABLE bands (
  id INT NOT NULL AUTO_INCREMENT,
  name VARCHAR(255) NOT NULL
  PRIMARY KEY (id)
);
```   