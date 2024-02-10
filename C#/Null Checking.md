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

## Null Coalescing

`??` operator returns the value of its left-hand operand if it isn't null, returns the right if otherwise

```csharp
int? myInt1 = 100;

int? myInt2 = myInt1 ?? 100;
Console.WriteLine(myInt2); // returns 100
```

`??=` assigns the value of its right-hand operand to its left-hand operand only if left-hand is null.

```csharp
int? myInt1 = null;

if(myInt1 is null) {
	myIn1 = 100;
}

myInt1 ??= 100;
```
