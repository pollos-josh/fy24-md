[[MySQL Day Two]]
[[Stored Procedure]]
---
# Begin... End
Code blocks
```sql
BEGIN
-- code
END
```

# IF... ELSE
Basically normal *if else* functionality
## Variable
```sql
DECLARE @Variable INT = 10;
IF @Variable > 5
	BEGIN
		PRINT 'The number is greater than 5';
	END
ELSE
	BEGIN
		PRINT 'The number is not greater than 5';
	END
```

# TRY... CATCH
*Used* for error handling and exception management.
```sql
CREATE PROCEDURE name
AS
BEGIN
	BEGIN TRY
		--code
	END TRY
	BEGIN CATCH
		--handle error
		PRINT'an error has occured: ' + ERROR_MESSAGE();
	END CATCH
END;
```