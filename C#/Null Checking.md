[[OOP]]
---

# Null Checking
## Null Forgiving
A postfix `!` operator. Suppresses all nullable warnings. Only affects compiler's static flow analysis, and has no effect on runtime.
```csharp
Console.WriteLine(value!.property); // disable compiler null checks

public string Property( get; set; ) = null!; //disables null checks
```

## Null Check
Checks whether reference type or nullable type is currently holding `NULL`.
```csharp
if (value == null)
{ 
	// 
}

if (value is null) {
	//
}

 if (value is not null) {
	//
}

 if (value?.Property == null) { // will check value if not null before checking object member
	//
}
```