USE Northwind

```SQL
--1.1
SELECT CustomerID, CompanyName, Address, City, Region, PostalCode, Country  FROM Customers
WHERE City = 'Paris' OR City = 'London';

--1.2
SELECT * FROM Products WHERE QuantityPerUnit Like '%Bottle%'

--1.3
SELECT CompanyName, Country FROM Suppliers

--1.4
SELECT p.CategoryID, p.ProductName
FROM Products p
ORDER BY p.CategoryID DESC

--1.5
SELECT e.TitleOfCourtesy, e.FirstName + ' ' + e.LastName AS 'Name',
e.City AS city
FROM Employees e
WHERE Country = 'UK'


--1.6
SELECT r.RegionID, FORMAT(SUM(od.UnitPrice * (1-od.Discount) * od.Quantity),'c') 'Total Discount Price'
FROM [Order Details] od
INNER JOIN Orders o  ON o.OrderID = od.OrderID
INNER JOIN EmployeeTerritories e ON o.EmployeeID = e.EmployeeID
INNER JOIN Territories t ON e.TerritoryID = t.TerritoryID
INNER JOIN Region r ON t.RegionID = r.RegionID
GROUP BY r.RegionID
HAVING (SUM(od.UnitPrice * (1-od.Discount) * od.Quantity)) > 1000000

--1.7
SELECT COUNT(o.OrderDate) AS 'Total Freight'
FROM Orders o
WHERE o.Freight > 100.00
OR o.ShipCountry= 'UK' OR o.ShipCountry= 'USA'


--1.8
SELECT Top 1 o.OrderID,
MAX(Discount)  AS 'Highest Discount',
ROUND(SUM(o.UnitPrice * (1-o.Discount) * o.Quantity), 2) AS 'Discounted Price'
FROM  [Order Details] o
GROUP BY o.OrderID
ORDER BY 'Highest Discount'DESC

--SELECT * [Order Details]


--2.1
USE Northwind

CREATE TABLE SpartansTable1
(
     name_id INT IDENTITY (1,1),
     title VARCHAR (4),
     firstName VARCHAR(20)NOT NULL,
     lastName VARCHAR(15),
     UniversityAttended VARCHAR(20),
     courseTaken VARCHAR (50),
     markAchieved INT,

)

INSERT INTO SpartansTable1

(
    title, firstName, lastName, UniversityAttended, courseTaken, markAchieved

)

VALUES

--2.2
(
  'Mr','James','Bond','Stafforshire','Film Production & Music Tech',1

)

DROP TABLE SpartansTable1;

SP_HELP SpartansTable
SELECT * FROM SpartansTable1

--3.1
SELECT e.FirstName + ' ' + e.LastName AS 'Employees', e. ReportsTo
FROM Employees e



--3.2
SELECT s.CompanyName,
ROUND(SUM(o.UnitPrice*(1-o.Discount)*o.Quantity),2) AS 'Total Sales'
FROM Products p

INNER JOIN Suppliers s ON p.SupplierID = s.SupplierID
INNER JOIN [Order Details] o ON p.ProductID = o.ProductID

GROUP BY s.CompanyName
HAVING SUM(o.UnitPrice*o.Quantity) > 10000
ORDER BY 'Total Sales'DESC

--3.3

SELECT TOP 10 c.ContactName, ROUND(SUM((UnitPrice*Quantity*(1-Discount))),2) AS "Total Value of Orders"
FROM Orders o
INNER JOIN Customers c ON o.CustomerID=c.CustomerID
INNER JOIN [Order Details] od ON o.OrderID=od.OrderID
WHERE o.ShippedDate BETWEEN '1998-01-01' AND '1998-05-06'
GROUP BY c.ContactName
ORDER BY "Total Value of Orders" DESC

--SELECT *
--FROM Orders
--ORDER BY ShippedDate

-- 3.4

SELECT AVG(DATEDIFF(dd, o.OrderDate, o.ShippedDate)) AS "Average Month"
FROM Orders o
GROUP BY MONTH(o.ShippedDate), YEAR(o.ShippedDate)

SELECT FORMAT(o.ShippedDate,'MM/yyyy'),
AVG(DATEDIFF(dd, o.OrderDate, o.ShippedDate)) AS "Average Days"
FROM Orders o
GROUP BY YEAR(o.ShippedDate),MONTH(o.ShippedDate), FORMAT(o.ShippedDate,'MM/yyyy')
ORDER BY YEAR(o.ShippedDate),MONTH(o.ShippedDate) ```
