[[OOP]]
---
# Interface
Represents a contract. It contains definitions for a group of related functionalities that a `class` or `struct` can implement.

It is a `custom type reference`.

```csharp
interface ISampleInterface {
	void SampleMethod();
}
```

```csharp
class SampleClass : ISampleInterface {
	public void SampleMethod() {
		//implementation
	}
}
```
## Interface Properties
- must implement all its members,
- cannot be instantiated directly
- can contain:
	- events
	- indexers
	- methods
	- properties
- contains no implementation
- a `class` or `struct` can implement multiple `interfaces`