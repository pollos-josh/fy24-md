# Properties
[[Classes]]
---

Flexible member that can read, write, or compute a value of a private field.

**Enables** public access for *get* and *set* while hiding implementation or verification.

```csharp
class SampleClass
{
	public int sampleProperty {get; set;}
}
```

```csharp
class SampleClass
{
	private int _sample;

	public int Sample {
		get {return _sample;}
	
		set {_sample = value;}
	}
}
```

*get* is used to return or get private sample.

*set* is used to store new value into sample.

Value is used to define the value being assigned by *set*.
