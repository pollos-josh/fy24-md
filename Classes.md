[[VS .NET]]
---
Functions like a user defined object. A blueprint and defines a behavior.
Declared with *class*.

```c#
class Currency {
	//fields, properties, methods, etc...
	public string currencyCode {get; set;}
	public string currencySymbol {get; set;}
}
```

New objects are created with:
```c#
Currency currencyName = new Currency();
```