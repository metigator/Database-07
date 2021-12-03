
-- [1]
-- Create a report that shows the CategoryName and Description 
-- from the categories table sorted by CategoryName.

    SELECT CategoryName, Description
	FROM northwind.categories
	ORDER BY CategoryName;
	
-- [2]
-- Create a report that shows the ContactName, CompanyName, ContactTitle and Phone number 
-- from the customers table sorted by ContactTitle DESC

	SELECT ContactName, CompanyName, ContactTitle, Phone
	FROM Customers
	Order By ContactTitle DESC

-- [3]
-- Create a report that shows the capitalized FirstName and 
-- capitalized LastName renamed as FirstName and Lastname 
-- respectively and HireDate from the employees table sorted 
-- from the newest to the oldest employee.

	SELECT UPPER(FIRSTNAME) AS FirstName, UPPER(LastName) As LastName, HireDate
	FROM Employees ORDER BY HireDate DESC;

-- [4]
-- Create a report that shows the top 10 OrderID, OrderDate, ShippedDate, CustomerID, Freight 
-- from the orders table sorted by Freight in descending order.

	SELECT TOP 10 OrderID, OrderDate, ShippedDate, CustomerID, Freight
	FROM orders
	ORDER BY Freight Desc;

-- [5]
-- Create a report that shows all the CustomerID in lowercase 
-- letter and renamed as ID from the customers table.

	SELECT LOWER(CustomerID) AS ID
	FROM Customers;
		
	
-- [6]
-- Create a report that shows the CompanyName, Fax, Phone, Country, HomePage 
-- from the suppliers table sorted by the Country in descending order then by 
-- CompanyName in ascending order.

	SELECT CompanyName, Fax, Phone,Country, HomePage
	FROM suppliers
	ORDER BY Country DESC, CompanyName;

-- [7]
-- Create a report that shows CompanyName, ContactName of all customers from ‘Buenos Aires' only.
 
-- [8]
-- Create a report showing ProductName, UnitPrice, QuantityPerUnit of 
-- products that are out of stock.
	
	SELECT ProductName, UnitPrice, QuantityPerUnit
	FROM products
	WHERE UnitsInStock = 0;
	
	
-- [9]
-- Create a report showing all the ContactName, Address, City 
-- of all customers not from Germany, Mexico, Spain.
	
SELECT ContactName, Address, City
FROM customers
WHERE Country NOT IN ('Germany','Mexico', 'Spain');


-- [10]
-- Create a report showing OrderDate, ShippedDate, CustomerID, Freight of 
-- all orders placed on 04 Feb 1997.

	SELECT OrderDate, ShippedDate, CustomerID, Freight
	FROM 
	Orders
	WHERE OrderDate = '1997-02-04';
	
	
-- [11]
-- Create a report showing FirstName, LastName, Country from the employees not from United States.

	SELECT FirstName,LastName,Country
	FROM employees
	WHERE Country <> 'USA';
	
	
12. -- [12]
-- Create a report that shows the EmployeeID, OrderID, CustomerID, RequiredDate, 
-- ShippedDate from all orders shipped later than the required date.

	SELECT EmployeeID,OrderID,CustomerID,RequiredDate,ShippedDate
	FROM Orders
	WHERE ShippedDate > RequiredDate;
	
	
-- [13]
-- Create a report that shows the City, CompanyName, ContactName of customers from 
-- cities starting with A or B.

	SELECT City, CompanyName, ContactName
	FROM Customers
	WHERE City LIKE 'A%' OR City LIKE 'B%';
	
	
-- [14]
-- Create a report showing all the even numbers of OrderID from the orders table

	SELECT OrderID
	FROM Orders
	WHERE OrderId % 2 = 0;


-- [15]
-- Create a report that shows all the orders where the freight cost more than $500
 
	 SELECT *
	 FROM  Orders
	 WHERE Freight > 500;
	 
-- [16]
-- Create a report that shows ProductName, UnitsInStock, UnitsOnOrder, ReorderLevel  when 
-- inventory items on hand quantity are below the reorder level.
	
	SELECT ProductName, UnitsInStock,UnitsOnOrder,ReorderLevel
	FROM Products
	WHERE UnitsInStock < ReorderLevel;

-- [17]
-- Create a report that shows the CompanyName, ContactName number of 
-- all customer that have no fax number
 
	SELECT CompanyName,ContactName,Fax
	FROM Customers
	WHERE Fax IS NULL;

-- [18]
--  Create a report that shows the FirstName, LastName of all employees 
-- that do not report to anybody

	SELECT FirstName, LastName
	FROM Employees
	WHERE ReportsTo IS NULL;
	
	
-- [19]
-- Create a report showing Products that we don't sell any more
	
	SELECT * 
	FROM Products 
	WHERE Discontinued = 1;
	
	
-- [20]
-- Create a report that shows the CompanyName, ContactName
-- Fax of all customers that do not have Fax number AND Live in USA and sorted by ContactName.
	
	SELECT CompanyName,ContactName,Fax
	FROM Customers
	WHERE Fax IS NULL AND Country = 'USA'
	ORDER BY ContactName;

-- [21]
-- Create a report that shows the City, CompanyName, ContactName of customers from cities that has 
-- letter L in the name sorted by ContactName.

	SELECT City, CompanyName, ContactName
	FROM
	Customers
	WHERE City like '%l%' 
	ORDER BY ContactName;

-- [22]
--  Create a report that shows the FirstName, LastName, BirthDate of employees born in the 1950s.

	SELECT
	FirstName, LastName, BirthDate
	FROM
	Employees
	WHERE BirthDate BETWEEN '1950-01-01' AND '1959-12-31'
	 
-- [23]
-- Create a report that shows the FirstName, LastName, the year of Birthdate as 
-- birth year from the employees table.
	
	SELECT LastName, FirstName, YEAR(Birthdate) AS BirthYear
	FROM Employees;
	
	
-- [24]
-- Create a report showing OrderID, total number of items in the order as NumberofItems 
-- from the orderdetails table grouped by OrderID and sorted by NumberofOrders in descending order. 

	SELECT OrderID, count(OrderID) as NumberofItems
	FROM [Order Details]
	GROUP BY OrderID
	ORDER BY NumberofItems DESC ;
	 
	 
-- [25]
-- Create a report that shows the SupplierID, ProductName, CompanyName 
-- from all product Supplied by 
-- Exotic Liquids, Specialty Biscuits, Ltd., Escargots Nouveaux sorted by the supplier ID 
 
	SELECT s.SupplierID, p.ProductName, S.CompanyName
	FROM Suppliers s
	JOIN Products p
	ON s.SupplierID = p.SupplierID
	WHERE s.CompanyName IN ('Exotic Liquids','Specialty Biscuits, Ltd.','Escargots Nouveaux')
	ORDER BY s.SupplierID;
	
-- [26]
-- Create a report that shows the 
-- ShipPostalCode, OrderID, OrderDate, RequiredDate, ShippedDate, ShipAddress of all orders
-- with ShipPostalCode ends with "00"
 
	SELECT * From Orders where ShipPostalCode like '%00';
 
-- [27]
--  Create a report that shows the ContactName, ContactTitle, CompanyName of customers that 
-- the has no "Sales" in their ContactTitle.

	SELECT ContactName, ContactTitle, CompanyName
	FROM
	Customers
	WHERE ContactTitle NOT LIKE '%sales%';

-- [28]
--  Create a report that shows the LastName, FirstName, City of employees 
-- in cities other "Seattle";

	SELECT
	LastName, FirstName, City
	FROM Employees
	WHERE CITY NOT IN ('Seattle');

-- [29]
--  Create a report that shows the CompanyName, ContactTitle, City, Country of all 
-- customers in any city in Mexico or other cities in Spain other than Madrid.
	
	SELECT CompanyName, ContactTitle, City, Country
	FROM Customers
	WHERE Country IN ('Mexico', 'Spain')
	AND City <> 'Madrid';
	
-- [30]
-- Create a select statement that outputs the following:
   photo 30
   
-- [31]
-- Create a report that shows the ContactName of all customers that do not have letter A as the second alphabet 
-- in their Contactname.
 
	SELECT ContactName
	FROM Customers
	where ContactName NOT like '_a%';
	
-- [32] 
--  Create a report that shows the average UnitPrice rounded to the next whole number, 
-- total of UnitsInStock and maximum number of pending orders from the products table. 
-- All saved as AveragePrice, TotalStock and MaxPendingOrders respectively.

	SELECT round (avg (UnitPrice),0) AS AveragePrice,
	SUM(UnitsInStock) AS TotalStock,
	max(UnitsOnOrder) as MaxPendingOrder
	FROM Products;

 
-- [33]
-- Create a report that shows the SupplierID, CompanyName, CategoryName, ProductName and UnitPrice 


	SELECT s.SupplierID, s.CompanyName, c.CategoryName, p.ProductName, p.UnitPrice
	FROM Products p
	JOIN Suppliers s
	ON s.SupplierID = p.SupplierID
	JOIN Categories C
	On c.CategoryID = p.CategoryID;

-- [34]
-- Create a report that shows the sum of Freight for each CustomerID, 
-- when sum of freight greater $200

	SELECT CustomerID, sum(Freight) TotalFreight
	FROM Orders
	GROUP BY CustomerID
	HAVING sum(Freight) > 200; 
	
-- [35]
-- Create a report that shows the OrderID ContactName, UnitPrice, Quantity
-- with discount given on every purchase.

 SELECT od.OrderID, c.ContactName,od.UnitPrice,od.Quantity,od.Discount
FROM [Order Details] od
JOIN Orders o
ON od.OrderID = o.OrderID
JOIN Customers c
ON c.CustomerID = o.CustomerID
WHERE od.Discount <> 0;  


-- [36]
-- Create a report that shows the EmployeeID, the LastName and FirstName as employee, 
-- and the LastName and FirstName of who they report to as manager sorted by Employee ID

	SELECT a.EmployeeID,
	CONCAT (a.LastName, ' ' ,a.FirstName ) AS Employee,
	CONCAT (b.LastName,' ', b.FirstName ) AS Manager
	FROM Employees a
	LEFT JOIN Employees b
	ON b.EmployeeID = a.ReportsTo
	ORDER BY a.EmployeeID;

-- [37]
-- Create a report that shows ProductId, ProductName, Active if discontinued is 0 otherwise 
-- InActive and name the column Status.

	SELECT ProductId, ProductName,
	CASE
		WHEN Discontinued = 0 THEN 'ACTIVE'
		ELSE 'INACTIVE'
	END
	AS Status
	FROM
	Products;


-- [38]
-- Create a view named CustomerInfo that shows the 
-- CustomerID, CompanyName, ContactName, ContactTitle, Address, 
-- City, Country, Phone, OrderDate, RequiredDate, ShippedDate.
 
	CREATE VIEW CustomerInfo AS
	SELECT C.CustomerID, C.CompanyName, C.ContactName, C.ContactTitle, C.Address,
	C.City,C.Country, C.Phone, O.OrderDate, O.RequiredDate, O.ShippedDate
	FROM
	Customers C
	INNER JOIN
	Orders O 
	ON C.CustomerID = O.CustomerID;
	
	
-- [39]
-- Change the name of the view you created from customerinfo to customer details.

	sp_rename @objname = 'dbo.CustomerInfo', @newname = 'CustomerDetails'


-- [40]
-- Create a view named ProductDetails that shows the 
-- ProductID, CompanyName, ProductName, CategoryName, 
-- Description, QuantityPerUnit, UnitPrice, UnitsInStock, UnitsOnOrder, ReorderLevel, Discontinued 

 
	 CREATE VIEW ProductDetails AS
	 SELECT 
	 P.ProductID, S.CompanyName, P.ProductName, C.CategoryName, 
	 C.Description, P.QuantityPerUnit, P.UnitPrice, P.UnitsInStock, P.UnitsOnOrder, P.ReorderLevel,
	 P.Discontinued 
	 FROM
	 Products P INNER JOIN
	 Suppliers S ON S.SupplierId = P.SupplierId
	 INNER JOIN Categories C ON C.CategoryID = P.CategoryID

-- [41] 
-- Drop the customer details view.

	DROP VIEW dbo.customerDetails;
	
	

-- [42] 
-- Create a report that fetch the first 5 character of categoryName from the category 
-- tables and renamed as ShortInfo

	 SELECT SUBSTRING(Description, 1, 5) AS ShortInfo
	 FROM
	 Categories;
	 
-- [43] 
-- Create a copy of the shipper table as shippers_duplicate. 
-- Then insert a copy of shippers data into the new table HINT: 
-- reate a Table, use the LIKE Statement and INSERT INTO statement.
  
	SELECT * INTO Shippers_Dup FROM Shippers; 

-- [44] 
-- ADD a cloumn to shippers_duplicate table called email of type varchar(150)
-- update each shipper email with random email to each shipper
-- and Display the data in the shippers_duplicate table

	ALTER TABLE Shippers_duplicate
	 ADD Email VARCHAR(150);


	 UPDATE Shippers_duplicate SET Email = 'speedyexpress@fake.com' where ShipperId = 1; 
	 UPDATE Shippers_duplicate SET Email = 'unitedpackage@fake.com' where ShipperId = 2;
	 UPDATE Shippers_duplicate SET Email = 'federalshipping@fake.com' where ShipperId = 3;

	 SELECT * FROM Shippers_duplicate;

-- [45] 
-- Create a report that shows the CompanyName and ProductName from all product 
-- in the Seafood category.
 

	 SELECT 
	 S.CompanyName, P.ProductName
	 FROM 
	 Products P INNER JOIN Categories C ON C.CategoryID = P.CategoryID
	 INNER JOIN Suppliers S ON S.SupplierID = P.SupplierID
		WHERE C.CategoryName = 'Seafood';
		
-- [46]
-- Create a report that shows most expensive and least expensive Product list (name and unit price)

	SELECT 
	ProductName, UnitPrice
	FROM Products
	WHERE UnitPrice = (SELECT MIN(UnitPrice) FROM Products) OR UnitPrice = (SELECT MAX(UnitPrice) FROM Products)
	GROUP BY ProductName, UnitPrice;

-- [47]
-- Delete the shippers_duplicate table.


	DROP TABLE Shippers_Duplicate;
 
48. Create a select statement that ouputs the following from the employees table.
    LastName, FirstName, Title, Age
	
	-- [48]
-- Create a select statement that ouputs the following from the employees table.
-- LastName, FirstName, Title, Age
 
	SELECT 
	LastName, FirstName, Title, 
	CONVERT(int, ROUND(DATEDIFF(hour,BirthDate,GETDATE())/8766.0,0)) AS Age from Employees;
	

-- [49]
-- Create a report that the CompanyName and total number of orders by customer
-- renamed as number of orders since Decemeber 31, 1994. Show number of Orders greater than 10.
 
	SELECT C.CompanyName, count(C.CustomerID) AS NumberofOrders
	FROM Customers C
	INNER JOIN Orders o
	ON O.CustomerID = C.CustomerID
	WHERE O.OrderDate >= '1994-12-31'
	GROUP BY C.CustomerID, C.CompanyName
	having COUNT(C.CustomerID) > 10;

-- [50]
-- Create a select statement that ouputs the following from the product table 
-- {ProductName} / is {quantityperunit} and cost ${unitprice}

SELECT CONCAT( ProductName,' weighs/is ' , QuantityPerUnit, ' and cost ','$', UnitPrice) AS ProductInfo
FROM Products;
  
