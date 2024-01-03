[[Classes]]
---
# Anonymous Type

Enables the creation of objects without writing a class definition for the data type. The type name is generated at compiler-level and not available in source code view.
```csharp
var sampleObject = new { Property1 = "first", Property2 = "second" };
```

It's mainly used for Temporary Data Structures and fast Testing and *Prototyping*.