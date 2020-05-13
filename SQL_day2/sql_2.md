# SQL DAY 2
### The order that matters when inserting is the one on the created …

### Leaving columns out you can always go back and insert.

### DEFAULT needs not be to mentioned but when editing it you have to be explicit about it.

## Variations on INSERT

### If you've already created the table, The order in which you add the data doesnt have to be the same as the original column order as long as the values match the order you are now inserting.

### VARCHAR, CHAR, DATE,

### Is NOT NULL but IS NULL. - NULL is not equal to zero - it means an undefined value.

### BIT - can only have zero or 1 ,true or false

### UPDATE function -

   SELECT * FROM jon_film_table
   UPDATE jon_film_table
   SET rating=10
   WHERE rating=5
  
### Delete function -If you need to remove rows from a table , use the DELETE statement. Beware of leaving out the WHERE clause, this will empty the entire table.

   
  DELETE FROM people
        WHERE person id=2 ```
        


# DATABASE Considerations
## Data Security
## Data Recovery
## Data Intergrity
## Normal Form

## ON DELETE CASCADE-AUTOMATIC
### DELETES THE ACTUAL PRIMARY KEY AND THE FOREIGN KEYS ASCOSSIATED WITH IT.

# Normal Forms
### 1NF(1st Normal Form)
0) A database is in the First Normal Form when the following conditions are satisfied:
0) Data must be presented as small as it can be.
0) There should be no repeating group
0)Every cell Every cell should contain one piece of Data and not have 2 cells in one box.

### 2NF
0)A table is in 2nd Normal Form if:
0)The table is in 1st normal form, and
0)All the non-key columns are dependent on the table’s primary key.

### 3NF
0)A database is in the Third Normal Form when the following conditions are satisfied:
0)It is in the 2NF
0)Theres no transitive functional dependancy i.e A transitive  functional Dependency is when a non-key column is functionally
dependent another non-key column , which is functinally dependent on the PRIMARY Key.

## Get rid of data redundancy is a date base ie duplicate values, we do it through 1st 2nd and 3rd normal form.

# Querying an SQL DATABASE
 
    
    SELECT * FROM Customers
    WHERE City='Paris'
    ```

### WHERE is used to filter the data
### City is the column The=Symbol operator
### Paris is the comparator
```SQL
``` SELECT COUNT(EmployeeID) AS "Number of Employees" FROM     Employees```
```
```-- use primary keys for counting rows --
SELECT COUNT(EmployeeID) AS "Number of Employees" FROM Employees```
```

## OTHER EXAMPLES
```SQL

SELECT CompanyName, City, Country, Region
FROM Customers WHERE Region='BC'

SELECT CustomerID, City FROM Customers
WHERE Country= 'France'

SELECT TOP 100 CompanyName FROM Customers WHERE Country='France'


SELECT COUNT(Discontinued) AS "Number of products"
FROM Products
WHERE Discontinued =1

SELECT CompanyName, City, Country, Region
FROM Customers WHERE Region='BC'

SELECT CustomerID, City FROM Customers
WHERE Country= 'France'

SELECT TOP 100 CompanyName FROM Customers WHERE Country='France'
```





### Short Cut
### THEN FROM Product p

### SQL READS FROM FIRST


### THEN GO AHEAD AND USE THE p. function to (avoid spelling errors)


```SQL
SELECT p.ProductName, p.UnitPrice
FROM Products p
WHERE p.CategoryID=1 AND p.Discontinued=0


INSTEAD OF:

SELECT ProductName, UnitPrice FROM Products
WHERE CategoryID= 1 AND Discontinued='0'```
```

### OR when one of the conditions are met

```


```
# Greater than
```SQL

SELECT ProductName, UnitPrice
FROM Products
WHERE UnitsInStock >0 OR UnitPrice > 29.99

SELECT ProductName, UnitPrice
FROM Products
WHERE UnitsInStock >0 AND UnitPrice > 29.99
```
<<<<<<< HEAD
### So WILD CARDS (%, _ , [charlist] , [^charlist])
```
=======
### So
``` SQL
>>>>>>> 88c7ff00e1a1031b3ce7c7738cd583b5352fe46c
SELECT DISTINCT cust.Country
FROM Customers cust
WHERE cust.ContactTitle='Owner' AND cust.Country LIKE '___I%'

SELECT DISTINCT cust.Country
FROM Customers cust
WHERE cust.ContactTitle='Owner' AND cust.Country LIKE [MS]%

```
# ^charlist
```SQL
SELECT DISTINCT cust.Country
FROM Customers cust
WHERE cust.ContactTitle='Owner' AND cust.Country LIKE [^MS]%
```
# 'Ch%' and more
```SQL
SELECT ProductName
FROM Products WHERE ProductNAme LIKE'Ch%'

SELECT *
FROM Customers c
WHERE c.Region LIKE '_A'

SELECT*
FROM Customers WHERE Region IN ('WA','SP')

```
# BETWEEN
```SQL
SELECT *
FROM EmployeeTerritories
WHERE TerritoryID BETWEEN 06800 AND 09999
```
# Less than <
```SQL
SELECT p.ProductName, p.ProductID
FROM Products p
WHERE p.UnitPrice < 5.00
```
# LIKE
``` SQL
SELECT * FROM Categories
WHERE CategoryName LIKE 'B%' OR CategoryName LIKE 'S%'
```
# IN
```SQL 
SELECT COUNT(o.OrderID) AS 'Number of orders'
FROM Orders o
WHERE EmployeeID IN (5,7)
```
# GROUPBY
``` SQL
SELECT o.EmployeeID, COUNT(*) AS 'NumberOfOrders'
FROM Orders o
GROUP BY EmployeeID
HAVING EmployeeID IN(5,7)

``` 
# CONCATENATION
``` SQL
SELECT c.CompanyName AS 'Company Name', c.City + ', ' + c.Country + 'City'
FROM Customers c

SELECT c.CompanyName AS "Company Name", CONCAT (c.City, ', ', c.Country)
FROM Customers c

SELECT e.FirstName + ', ' + e.LastName AS "Employee NAME"
FROM Employees e

```
# IS NOT NULL
``` SQL
SELECT Region, c.CompanyName AS 'Company Name', c.City + ', ' + c.Country + 'City'
FROM Customers c WHERE Region IS NOT NULL

```

``` 
SELECT c.Region, c.Country
FROM Customers c    
WHERE c.Region IS NOT NULL

```
# DISTINCT
``` SQL
SELECT DISTINCTc.Region, c.Country
FROM Customers c    
WHERE c.Region IS NOT NULL```
