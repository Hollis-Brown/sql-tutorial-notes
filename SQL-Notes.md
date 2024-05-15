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
#### Review
- The inside of the parentheses is for defining the different columns
  - `id` provides a unique identification number.
  - `INT` specifies that the id's characters will be a number.
  - `NOT NULL` specifies that the id number can never be empty.
  - `AUTO_INCREMENT` specifies that each newly added (album) item will automatically be incremented. 
***

#### What are the commands to tell SQL that you want to create an albums table and columns therein? 
```sql
CREATE DATABASE record_company;
USE record_company;
CREATE TABLE bands (
  id INT NOT NULL AUTO_INCREMENT,
  name VARCHAR(255) NOT NULL
  PRIMARY KEY (id)
);
CREATE TABLE albums (
  id INT NOT NULL AUTO_INCREMENT,
  name VARCHAR(255) NOT NULL,
  release_year INT,
  band_id INT NOT NULL,
  PRIMARY KEY (id)
);
```  

At this point the syntax is should become pretty self-explanatory however, the `release_year INT`clause of the code is important to unpack. It does not include the keyword `NOT` and/or `NULL` because I don't know when the album will be released. I need to be able to connect an album to a band and I can't just put a band column inside of album column. I need to be able to reference the `bands` table from inside of the `album` table. That's why the id inside of the `bands` table comes in handy because I can save it inside of the `albums` table as a reference to the `bands` table from within the `albums` table. There I'll add a `band_id` column. 
***
#### What does this code do?
```sql

-- Add a single band/value to a table at a time
INSERT INTO bands (name)
VALUES ('Iron Maiden');

-- Alternative way to add multiple bands/values to a table at once
INSERT INTO bands (name)
VALUES ('Deuce'), ('Avenged Sevenfold'), ('Ankor');

-- Query all of the newly added bands
SELECT *
FROM bands;

-- Query the bands table limited to just two rows
SELECT *
FROM bands
LIMIT 2;

-- Query only the name column
SELECT name
FROM bands;

-- Use `AS` to alias column names
SELECT id AS 'ID', name AS 'Band Name' 
FROM bands;

-- Query to put bands in (default) ascending order
SELECT *
FROM bands
ORDER BY name;

-- Query to put bands in descending order
SELECT *
FROM bands
ORDER BY name DESC;

-- Add some albums into table
INSERT INTO albums (name, release_year, band_id)
VALUES ('Some nonsense', 1985, 1),
	   ('Somemore nonsense', 1984, 1),
       ('Even more nonsense', 2018, 2),
       ('Even more nonsense', 2010, 3),
       ('Test Album', NULL, 3);
       
-- Query the newly added albums
SELECT *
FROM albums;

-- Query only the name column to demonstrate a problem of redundancy as an intro
-- to a keyword command to remove redudancies
SELECT name
FROM albums;

-- What do I do if I just want `unique` names and not `all` the names?
-- You can use the `DISTINCT` keyword command!
SELECT DISTINCT name
FROM albums;

-- What does `DISTINCT` do?
-- `DISTINCT` takes all the data that is returned and compares them, identifying if 
-- any of the data is the same and if so, it removes the redundancies leaving only
-- only the `unique` names; it leaves only one `unique` column instead of duplicates. 


```