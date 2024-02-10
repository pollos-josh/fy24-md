[[Bootcamp Notes]]
---
# ADO .NET

Allows devs to interact with databases, read and write data, and perform typical database actions.

## [[CSharp SQL Syntax]]
## Data Providers

Specific libraries provided by Microsoft to facilitate data access and interaction with database systems.

## Data Set

### Connection String

```csharp
string connectionString = "Data Source =.; Initial Catalog = DemoDatabase; Integrated Security = True"; 
```

## Delegate

A type that represents references to methods with a particular parameter list and return type. When you instantiate a delegate, you can associate its instance with any method with a compatible signature and return type.

```csharp
delegate int myDelegate(int a, int b);

class Calculator {
	public static int Add(int a, int b) {
		return a + b;
	}

	public static int Minus(int a, int b) {
		return a - b;
	}
}
```

It's a way to quickly call methods.

```csharp
public class Program {
	public static int PerformOperation(int x, int y, myDelegate operation){
		return operation(x, y);
	}
	
	public static void Main(string[] args) {
		
		Calculator calculator = new Calculator();
		
		myDelegate add = calculator.Add;
		myDelegate subtract = calculator.Minus;
		
		int resultAdd = (10, 5, add);
		int resultSubtract = (10, 5, subtract);
	}
}
```

# [[Lambda Expression]]

# [[ADO.NET Entity Framework]]
---
# Best Practices
- Don't hardcode connection string in source code. It should be in `appsettings.json` with other configuration settings/files.
