# SQL 4

# SUb query
```SQL
SELECT c.CompanyName FROM Customers c
WHERE c.CustomerID IN
(SELECT o.CustomerID FROM Orders o)
```

## Or Use Join
```SQL
SELECT DISTINCT c.CompanyNAme FROM Customers c
INNER JOIN Orders o ON o.CustomerID=c.CustomerID

SELECT o.OrderID, o.ProductID, o.UnitPrice, o.Quantity,
(SELECT MAX(UnitPrice) FROM [Order Details]) AS 'MAX PRICE'
FROM [Order Details]o
```

## More SubQuery
```SQL
SELECT o.OrderID, o.ProductID, o.UnitPrice, o.Quantity
FROM [Order Details]o
WHERE o.ProductID IN
(SELECT p.ProductID FROM Products p WHERE p.Discontinued=1)
```

## UNION
```SQL
--UNION/ALL UNION

SELECT EmployeeID AS 'Employee/Supplier'
FROM Employees
UNION ALL
SELECT SupplierID
FROM Suppliers
```
