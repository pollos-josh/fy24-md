[[Classes]]
---
# Exceptions
Code that is thrown when there are errors. Derived from `System.Exception`.

```csharp
class CustomException : Exception {
	public CustomException(string message) {
	}
}
```

## Exception Handling
Allows you to gracefully handle any unexpected or exceptional situations. Uses the `try`, `catch`, and `finally`.

`try` block wrap code that might result in exceptions.
`catch` will handle any resulting errors.
`finally` will run whether or not an exception occurs.