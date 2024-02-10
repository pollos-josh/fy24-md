[[Bootcamp Notes]]
[[MySQL Day One]]
---

# Joins

**Inner Join** - Returns joins that have matching values in both tables

**Left Join** - All rows in left table and matching rows in right table

**Right Join** - All rows in right table and matching rows

**Full Join** - All records where there is a match in left and right tables

Join | Description
--- | --- 
Inner Join | Returns matching values in both tables
Left Join | All rows in left table, matching tables in right table
Right Join | All rows in right and matching rows on left
Full Join | All rows

## Inner Join

```Sql
SELECT p.Name, SUM(p.ListPrice) AS TotalPrice, pc.Name
FROM SalesLT.Product AS P
INNER JOIN SalesLT.ProductCategory AS PC
ON p.ProductCategoryID = pc.ProductCategoryID
GROUP BY p.Name, pc.Name
```

*above code joins SalesLT.ProductCategory to SalesLT.Product on the FK ProductCategoryID*

Set 1 | Set 2
--- | ---
Item 1 | Item3
Item 2 | Item 4
Item 3 | Item 5
Item 4 | Item 6

```sql
SELECT * A INNER JOIN B ON AA = BB
```

AA | BB
--- | ---
Item 3| Item 3
Item 4 | Item 4

## Left Join

```sql
SELECT * A LEFT JOIN B ON AA = BB
```

Set 1 | Set 2
--- | ---
Item 1 | Item3
Item 2 | Item 4
Item 3 | Item 5
Item 4 | Item 6

AA | BB
--- | ---
Item 1 | - |
Item 2 | - |
Item 3 | Item 3
Item 4 | Item 4

## Right Join

```sql
SELECT * A RIGHT JOIN B ON AA = BB
```

Set 1 | Set 2
--- | ---
Item 1 | Item3
Item 2 | Item 4
Item 3 | Item 5
Item 4 | Item 6

**AA**|** BB**
-----|-----
Item 3| Item 3
Item 4| Item 4
-| Item 5
-| Item 6

## Full Join

Set 1 | Set 2
--- | ---
Item 1 | Item3
Item 2 | Item 4
Item 3 | Item 5
Item 4 | Item 6

```sql
SELECT * FROM A FULL JOIN B ON AA = BB
```

| AA     | BB     |
| ------ | ------ |
| Item 1 | -      |
| Item 2 | -      |
| Item 3 | Item 3 |
| Item 4 | Item 4 |
| -      | Item 5 |

## Union

Combine results of two queries

```sql
SELECT column1, column2 FROM table1
UNION
SELECT column1, column2 FROM table2
```

This basically dumps table2 data on table1 table.

## Union All

Combine results of two queries with duplicates

```sql
SELECT column1, column2 FROM table1
UNION ALL
SELECT column1, column2 FROM table2
```

## View

Temporary table defined by queries

```sql
CREATE VIEW view_name
AS
SELECT column1, column2 FROM table;
```

```sql
ALTER VIEW view_name
AS
SELECT column1, column2, column3 FROM table WHERE column1 = 'value'
```

```sql
DROP VIEW view_name
```

Views also function as normal tables

```sql
SELECT * FROM view_name
```

*Views are most often used when joining multiple tables*

---

[[Programmability]]

[[Stored Procedure]]

[[User-Defined Function]]

---
