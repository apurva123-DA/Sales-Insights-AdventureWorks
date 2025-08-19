# Sales Insights Project (AdventureWorks)

📄 [View Full Project Report (PDF)](./Sales_Insights_Project.pdf)

This project analyzes sales data using SQL & Power BI...

-- 1. Total Sales by Year
SELECT YEAR(OrderDate) AS SalesYear,
       SUM(UnitPrice * OrderQty) AS TotalSales
FROM Sales.SalesOrderDetail sod
JOIN Sales.SalesOrderHeader soh
  ON sod.SalesOrderID = soh.SalesOrderID
GROUP BY YEAR(OrderDate)
ORDER BY SalesYear;

-- 2. Top 5 Customers by Revenue
SELECT TOP 5 c.CustomerID,
       SUM(sod.UnitPrice * sod.OrderQty) AS Revenue
FROM Sales.SalesOrderDetail sod
JOIN Sales.SalesOrderHeader soh ON sod.SalesOrderID = soh.SalesOrderID
JOIN Sales.Customer c ON soh.CustomerID = c.CustomerID
GROUP BY c.CustomerID
ORDER BY Revenue DESC;

-- 3. Sales by Product Category
SELECT p.Name AS Product,
       SUM(sod.UnitPrice * sod.OrderQty) AS TotalSales
FROM Sales.SalesOrderDetail sod
JOIN Production.Product p ON sod.ProductID = p.ProductID
GROUP BY p.Name
ORDER BY TotalSales DESC;

POWERBI WORK
Load the AdventureWorks dataset (CSV or SQL Server sample DB).

Create visuals:

Bar chart → Sales by Year

Pie chart → Revenue share by Top Customers

Tree map → Sales by Product Category

Card → Total Sales KPI

Save it as Sales_Insights.pbix.

