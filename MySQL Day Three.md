[[Bootcamp Notes]]
[[MySQL Day Two]]
---

# Server Profiler
Microsoft tool to analyze and monitor activities and performance tuning of SQL Server databases.

# CRUD
C - Create New Record
R - Read / Retrieve / Query
U - Update / Edit
D - Delete


## Practice
1. Write a SQL statement using INNER JOIN to know which salesman are working for which customer.

```sql
CREATE TABLE [dbo].[Customer] (
	CustomerID INT IDENTITY(1,1) NOT NULL PRIMARY KEY,
	CustomerName VARCHAR(20) NOT NULL,
	AccountNumber NCHAR(10) NOT NULL,
	SalesPersonID INT NOT NULL
)
```
*create customer table with sales person id*

```sql
CREATE TABLE [dbo].[SalesPerson] (
	SalesPersonID INT IDENTITY(1,1) NOT NULL PRIMARY KEY,
	SalesPersonName VARCHAR(20) NOT NULL,
	SalesQuota MONEY,
	SalesYTD MONEY
)
```
*create sales person table*

```sql
ALTER TABLE [dbo].[Customer]
ADD CONSTRAINT sales_relation [SalesPersonID] FOREIGN KEY REFERENCES [dbo].[SalesPerson](SalesPersonID)
```
*bridge customer and sales person table*

```sql
SELECT c.[CustomerName], c.[AccountNumber], s.[SalesPerson] AS SalesPerson
FROM [dbo].[Customer] AS c
JOIN [dbo].[SalesPerson] AS s ON c.[SalesPersonID] = s.[SalesPersonID]
```

**CustomerName**|**AccountNumber**|**SalesPerson**
-----|-----|-----
Catherine Abel|AW00000293|Tom Reiter
Kim Abercrombie|AW00000295|Michael Blythe
Kim Abercrombie|AW00000038|Jillian Carson
Humberto Acevedo|AW00000297|Jillian Carson
Gustavo Achong|AW00000299|Garret Vegas
Pilar Ackerman|AW00000305|Linda Mitchell
Carla Adams|AW00000305|David Campbell
Amy Alberts|AW00000287|Michael Blythe

---
2. Write a SQL statement without using JOIN to prepare a list with salesman name, customer name and their TerritoryID for the salesmen and customer who belongs to the same TerritoryID.

```sql
ALTER TABLE [dbo].[Customer] ADD [TerritoryID]
ALTER TABLE [dbo].[SalesPerson] ADD [TerritoryID]
```
*add new TerritoryID column*

```sql
SELECT s.[SalesPersonName], c.[CustomerName], c.[TerritoryID]
FROM [dbo].[Customer] AS c, [dbo].[SalesPerson] AS s
WHERE s.[TerritoryID] = c.[TerritoryID]
```

**SalesPersonName**|**CustomerName**|**TerritoryID**
-----|-----|-----
Garret Vegas|Catherine Abel|2
Michael Blythe|Gustavo Achong|3
Tom Reiter|Gustavo Achong|3
Jillian Carson|Kim Abercrombie|5
David Campbell|Carla Adams|7
