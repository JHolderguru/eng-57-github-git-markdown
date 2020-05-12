# SQL Day One

### Database- a structured set of data held in a computer especially one that is accessible in various ways.

# Relational Database

### Through a column (first name and last name customer id makes it unique because customers can have a similar names(Customer ID is the unique field in the customers table (PK Primary KEY). Defining the relationship between the two tables.(Foreign key) .

### One to ONE (cant have more than one NHsID )

### One to Many(one customer can have many receipts and many purchase ids)

### Many to Many (the course can be accessed by many students)

### For the sake of Retrieving Data  we do a Junction table to simplify

### It takes the primary key from both tables and puts it the middle and they become COMPOSITE KEYS (studentID, courseID)

## PRIMARY KEY Value must never change…maximum one primary.

### CANDIDATE KEYS (any can be a primary key) dependant on the admin<<

### Foreign key has to be one of the values pointing to one of data it relates to:

# DATABASE TOOLS


### -Access
### – SQL server Editions
### – PostgreSQL( the way of writing the SQL is different, this is open source)
### -SQLite (easier to use the database) is good for lite weight) small fast reliable)

### – MySQL similar to Azure- redis (very fast and uses key value mapping but it isn’t fully flerged

### – MongoDB is used a lot for Big Data uses JSON (search JSON) using mongo you can store the DATA , there are pros and Cons, it’s a non relational Database.

### – Oracle is the most used and its at the top.


# STRUCTURED QUERY LANGUAGE

### DML – To Manipulate the DATA**
### DDL- Data Definition Language -Manipulate the DATA structure(create, alter, drop, truncate-data def language that is to Delete ALL DATA from a Table)**
### DCL – (Temp access to what you need to do the Job (selecting retrieve inserting(checked) deletion(nope) immediately revoked after assignment)
### TCL- Transaction Commit Language -Commit to the changes, ### Database all the work you have done, you also have rollback to undo. Save point but not yet committing.

# DATA TYPES

### VARCHAR is adaptable----it will take what it needs
### CHAr is fixed ( very bad in terms of memory, it still needs what is set)
### If char is so bad with memory why keep it – because CHAR is 50% than VARCHAR in retrieving DATA.(VARCHAR needs to calculate and determine)

### INT – holds a whole  number/interger calue(see also bigint,smallint and tinyint)positive of negative.
### as you are placing the int you need to consider the future, when designing the database and decided what type to use

### DATE or TIME or DATETIME

### DECIMAL

### BINARY - fixed Precision and scale (digits to right of decimal point) numbers.

### FLOAT - scientific use (very large numbers)

### BIT - equivalent to binary (0,1 or NULL)


# DATABASE Practice

 USE Northwind


 SP_HELP Customers

 USE jonholder_db

 ```CREATE TABLE jon_film_table
  (    
   film_id INT IDENTITY (1,1),
   film_name VARCHAR(20),
   film_type VARCHAR (12),
   date_of_release DATETIME,
   director VARCHAR (20),
   writer VARCHAR (20),
   star VARCHAR (20),
   film_language VARCHAR(10),
   official_website VARCHAR (50),
   plot_summary VARCHAR (MAX)

 );
 /* bla bla* /
 -- bla bla--

 SP_HELP jon_film_table


DROP TABLE jon_film_table;

 SP_HELP jon_film_table;

 ALTER TABLE jon_film_table ADD film_id INT;

 SP_HELP jon_film_table

 ALTER TABLE jon_film_table
 DROP COLUMN film_type;

 SP_HELP jon_film_table

 (
     film_name, director, plot_summary
 )
 VALUES
(    'THE MATRIX', 'WACHOWSKI BROTHERS', 'A computer hacker learns from mysterious rebels about the true nature of his  reality and his role in the war against its controllers.'

 ),
 (
    'MATRIX REVOLUTIONS', 'WACHOWSKI BROTHERS','A    computer  hacker is back in the war controllers fighting them to the ultimate city of Zion.'
 )


 SELECT* FROM jon_film_table

 ALTER TABLE jon_film_table
 DROP COLUMN film_id

 ALTER TABLE jon_film_table
 DROP COLUMN film_name

 ALTER TABLE jon_film_table
 ADD film_name VARCHAR(20);

 SP_HELP  ```
