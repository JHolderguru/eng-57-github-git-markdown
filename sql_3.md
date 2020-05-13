# SQL DAY3.

``` MarkDown


```

```SQL


SELECT * FROM [Order Details]

SELECT o.UnitPrice, o.Quantity, o.Discount,
o.UnitPrice * o.Quantity  AS 'Gross Total',
 o.UnitPrice * o.Quantity * (1-o.Discount) AS 'Net Total'
FROM [Order Details] o

In laymans term
o.UnitPrice   * o.Quantity  -   o.UnitPrice  * o.Quantity  * o.Discount AS ‘Net total’

--TO GET THE ORDER BY DESCENDING

SELECT * FROM [Order Details]

SELECT o.UnitPrice, o.Quantity, o.Discount,
o.UnitPrice * o.Quantity  AS 'Gross Total'
 o.UnitPrice * o.Quantity * (1-o.Discount) AS 'Net Total'
FROM [Order Details] o
ORDER BY 'Net total'DESC


--TO GROUP BY

SELECT * FROM [Order Details]

SELECT o.UnitPrice, o.Quantity, o.Discount,
SUM(o.UnitPrice * o.Quantity ) AS 'Gross Total',
FROM [Order Details] o
GROUP BY o.OrderID,o.UnitPrice,o.Quantity, o.Discount
ORDER BY 'GROSS total'DESC

--TOP of the list

--USE ORDER BY to IDENTIFY the highest NET Total in the order table details table?
--(order by is doing the sorting)
--(DESC is Descending)

SELECT TOP 2 o.UnitPrice, o.Quantity, o.Discount,
o.UnitPrice * o.Quantity *(1 - o.Discount) AS 'Net Total'
FROM [Order Details] o
ORDER BY 'Net total' DESC

--CHARINDEXING

SELECT * FROM Customers

SELECT c.PostalCode AS 'PostCode',
LEFT (c.PostalCode, CHARINDEX(' ', c.PostalCode)-1) AS 'Postal Code Region',
     CHARINDEX('', c.PostalCode) AS 'Space found', Country
FROM Customers c
WHERE Country='UK'


-- Printing Apostophe

SELECT * FROM Products

SELECT p.ProductName
FROM Products p
WHERE p.ProductName LIKE '%''%'


-- Char index will never return zero

SELECT p.ProductName
FROM Products p
WHERE CHARINDEX('''', p.ProductName)>0

--Date functions

SELECT DATEADD(d,5,OrderDate) AS 'Due Date'
DATEDIFF(d,OrderDate, ShippedDate) AS 'Ship Days'
From Orders

SELECT * FROM Employees
SELECT FirstName + ' ' + LastName AS 'Name'
DATEDIFF (yyyy, BirthDate, GETDATE()) AS 'Age'
FROM Employees


-- case to investigate(exercise CASE to add a column to the previous activity solution call retirement according to)
--1.Age greater than 65='Retired'
--2.Age greater than 60='Retirement due'
--3.Age greater than 60='More than 5 years to go'

SELECT DATEDIFF (yyyy, BirthDate, GETDATE()) AS 'Age',
CASE
WHEN DATEDIFF (yyyy, BirthDate, GETDATE())> 65
THEN 'Retired'
WHEN DATEDIFF (yyyy, BirthDate, GETDATE())> 60
THEN 'Retirement Due'
ELSE 'More than 5 years to go'
END AS 'Retirement Status'
FROM Employees;


--Sum
SELECT * FROM Products

SELECT SUM (p.UnitsOnOrder) AS 'Total Order',
AVG (p.UnitsOnOrder) AS 'Total Order',
MIN (p.UnitsOnOrder) AS 'Total Order',
MAX (p.UnitsOnOrder) AS 'Total Order'
FROM Products p

-----GRoup BY SupplierID
SELECT * FROM Products

SELECT SUM (p.UnitsOnOrder) AS 'Total Order',
SUM (p.UnitsOnOrder) AS 'Total Order',
AVG (p.UnitsOnOrder) AS 'AVG Order',
MIN (p.UnitsOnOrder) AS 'MAX Order'
FROM Products p
GROUP BY p.SupplierID

--GRoup by -- Use GROUP BY to calculate the average Reorder level
---for  all  Products by category ID

SELECT p.CategoryID,
AVG(p.ReorderLevel) AS 'avg on reorder level'
FROM Products p

GROUP BY p.CategoryID


--select the highest (add TOP 1 and ORDER BY)
SELECT TOP 1 p.CategoryID,
AVG(p.ReorderLevel) AS 'avg on reorder level'
FROM Products p

GROUP BY p.CategoryID
ORDER BY 'avg on reorder level' DESC


```
MarkDown

# JOINS
INNER JOIN IS TAKING THE COMMON AND JOINING THEM.

```SQL
--joins

SELECT p.SupplierID, s.CompanyName AS 'Supplier Name',
AVG (p.UnitsOnOrder) AS 'Average Units on Order'
FROM Products p  INNER JOIN Suppliers s
ON p.SupplierID=s.SupplierID
GROUP BY p.SupplierID , s.CompanyName

SELECT * FROM Suppliers```

```SQL
-- multipe join
SELECT p.ProductName,p.UnitPrice,s.CompanyName AS 'Suppliers',
C.CategoryID AS 'Category '
FROM Products p
INNER JOIN Suppliers s ON p.SupplierID=s.SupplierID
INNER JOIN Categories c  ON  p.CategoryID=c.CategoryID```


```
``` MarkDown
INDEXING IN SQL STARTS FROM ONE NOT ZERO

Substring (jonathan 1,1)
Would be JJ (start point and the one after)

CHARINDEX (‘a’,’Ashraf’) WILL RETURN 1
           (‘a’, ‘Rayam’) WILL RETURN 2

LEFT OR RIGHT
SELECT RIGHT("SQL Tutorial", 3) AS ExtractString; =ial
SELECT LEFT("SQL Tutorial", 3) AS ExtractString; =SQL

LEN = length

SELECT REPLACE
SELECT REPLACE(‘SQL tutorial, SQL, HTML) = HTML Tutorial

SELECT LOWER (HTML)
=html

--SELECT UPPER(html)
=HMTL

--SELECT SUBSTRING
SELECT SUBSTRING('my book', 4, 3) AS ExtractString;
=BOO
SELECT SUBSTRING('my book', 1, 3) AS ExtractString
=my


DATE funtions
returns the date time of the computer being used.
