[[Bootcamp Notes]]
---
## Constraints
- NOT NULL
- UNIQUE
*ALTER*
- For editing column constraints/datatype
*CTRL+K, CTRL+X*
- Command pallete
## INDEX
- Used to speed up query process.
- A special lookup table that the database uses to speed up data retrieval.

1. *Clustered* - Only one clustered table per database
```sql
CREATE CLUSTERED INDEX index1
ON table_name(column_name)
```
2. *Non-Clustered*
	- Stored at one place and table data is stored in another place
	- CREATE INDEX index1 ON table_name.column_name
	- Can be multiple
	- Data is arranged in another table

# Auto-Increment
- Allows a unique number to be generated automatically
- Only one identity per table

```SQL
CREATE TABLE table_name (
Column1 INT IDENTITY(initial value, increment value) PRIMARY KEY,
Column2 datatype
);

```

# Truncate Table
- Clear table contents

# Reseed Table (not advisable)
- DBCC CHECKIDENT ('[dbo].[SampleTable]', RESEED, 0);
- Resets increment for table records to specified number

# SQL Commands
## Select
- Selects data
```SQL
SELECT *
FROM table_name
``` 
## Insert
- Inserts data into a table
```sql
 INSERT INTO table_name(column1, column2) VALUES ('string', int)
 ```
 
## Update
- Update a record
 ```sql
 UPDATE table_name SET column_name = 'value' WHERE condition
```

## Delete
- Delete a record
- Ideally use a WHERE clause
```SQL
DELETE FROM table_name WHERE 'condiiton'
```

## Alias
- used to give a table or column a temporary name
- useful with joins
```SQL
SELECT c.[CustomerID], c.[FirstName], c.[LastName]
FROM [dbo].[Customer] AS c
```

## Distinct
- returns distinct values
```sql
SELECT DISTINCT column1, column2
FROM table_name
```

## Where
- Used to filter records
- Comes *after* FROM clause
- Can use math operators
```SQL
SELECT * FROM [SalesLT].[Product]
WHERE [Color] = 'RED' OR [Color] = 'SILVER'
```

```sql
SELECT [ProductID],[Name],[ListPrice] FROM [SalesLT].[Product]
WHERE [ListPrice] >= 500
```

- **BETWEEN AND**
	- Displays a record if column value is between two values
- *LIKE*
	- Displays if match is true
- **IN**
	- Displays record if column value has any of the values in the list
	- Decreases the use of OR
```sql
SELECT [ProductID], [Name], [ListPrice], [Color] FROM [SalesLT].[Product]
WHERE [Color] IN ('Red','Black','Multi')
```
- *IS*
	- Displays a record for values that might be NULL
 ```sql
 SELECT *
 FROM table_name
 WHERE [Color] IS NULL;
```

![[Pasted image 20231212143341.png]] 
## NOT
- basically NOT gate. Reverse logic
- *NOT*
- *<>*
- *!=*
```sql
SELECT *
FROM table_name
WHERE NOT [color] = 'red'
```

## ORDER BY
- sort
- *ASC*
 - *DESC*


# Aggregate Functions

- Count
```sql
SELECT COUNT(record) FROM table
```
*returns the number of records*

- Max
```sql
SELECT MAX(record) FROM table
```
*returns the highest value in column*

- Min
```sql
SELECT MIN(record) FROM table
```
*returns the smallest value in column*

- Sum
```sql
SELECT SUM(record) FROM table
```
*returns summation of column*

- Avg
```SQL
SELECT AVG(record) FROM table
```
*returns average value of column*

---
## GROUP BY
- combines rows into groups based on matching values in specifics columns
```sql
SELECT [Color] FROM table
GROUP BY [Color]
```

```sql
SELECT [Color], COUNT([Color]) AS COLOR_COUNT, SUM([ListPrice]) AS TOTAL_PRICE
FROM [SalesLT].[Product]
WHERE [Color] IS NOT NULL
GROUP BY [Color]
ORDER BY [COLOR_COUNT]
```
*returns count and summation by color*

## HAVING
alternative to WHERE clause for Aggregate functions
``` sql
SELECT COUNT(CustomerID), Country  
FROM Customers  
GROUP BY Country  
HAVING COUNT(CustomerID) > 5  
ORDER BY COUNT(CustomerID) DESC;
```
---
[[Table Normalization and Functional Dependency]]
[[MySQL Day Two]]