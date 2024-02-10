# Stored Procedure
[[MySQL Day Two]]
---

Contains one or more SQL statements. It can also take input statements and return output parameters.

```sql
CREATE PROCEDURE procedure_name
AS
SELECT column1, column2 FROM table_name
GO;
```

Execute code with

```sql
EXEC procedure_name [params]; -- or EXECUTE
```

Adding parameters

```sql
ALTER PROCEDURE dbo.spProductInsert
@Name nchar(20),
@Price MONEY

AS
	INSERT INTO [dbo].[Products]
		([Name],[Description],[Price])
	VALUES
		(@Name, 'this is a sample product description.', @Price)

EXEC spProductInsert @Name=2, @Price=13
```

*Basically an SQL function*.

---

[[Programmability]]

[[User-Defined Function]]
