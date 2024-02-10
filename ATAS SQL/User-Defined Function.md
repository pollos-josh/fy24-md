# User-Defined Function

[[Stored Procedure]]

[[Bootcamp Notes]]

[[MySQL Day Two]]

---

Allows user to encapsulate a reusable piece of logic and computation. UDFs are user-created functions that can take zero or more input parameters. It returns a single value (Scalar UDF) or table values (Table-Valued UDF).

```sql
CREATE FUNCTION function_name (parameters)
RETURNS datatype AS
BEGIN
	statements
	RETURN value
END;
```

## Scalar UDF Example

```sql
CREATE FUNCTION udfDiscountedProduct (
	@Price MONEY
)
RETURNS MONEY AS
BEGIN
	RETURN @Price * .5
END;
```

*Can be performed within queries*

*Can perform math operations*

## Table-Valued UDF Example

```sql
CREATE FUNCTION udfProductTable(@MinPrice MONEY, @MaxPrice MONEY)
RETURNS TABLE
AS
	RETURN SELECT * FROM [dbo].[Products] WHERE [Price] BETWEEN @MinPrice AND @MaxPrice
```

```sql
SELECT * FROM udfProductTable(5, 100)
```
