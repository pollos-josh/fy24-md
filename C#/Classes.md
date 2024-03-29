[[VS .NET]]
---
# Classes

Functions like a user defined object. A blueprint and defines a behavior.

Declared with *class*.

```csharp
class Currency {
	//fields, properties, methods, etc...
	public string currencyCode {get; set;}
	public string currencySymbol {get; set;}

	public Currency(string code, string symbol) {
		currencyCode = code;
		currencySymbol = symbol;
	}
}
```

New objects are created with:

```csharp
Currency unitedStatesCurrency = new Currency("USD","$");
Currency philippinesCurrency = new Currency("PHP", "₱");

Console.WriteLine(currency.philippinesCurrency.code)
Console.WriteLine(currency.philippinesCurrency.symbol)
```

## Class Vs Struct

Classes are more based. You can put a lot more fields, properties, etc., in classes than in structs.

Structs are smaller and faster in memory.

## Members
- [[Fields]]
- [[Constants]]
- [[Properties]]
- [[Methods]]
- Events
- Operators
- Indexers
- [[Constructors]]
- Destructors
- [[Nested Types]]
- [[Static]]
- [[Anonymous Type]]
- [[Enum]]
- [[Exceptions]]
