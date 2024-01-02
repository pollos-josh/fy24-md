[[Classes]]
---
Class objects that are executed automatically when an object of a given type is created.

Usually initializes the data members of the new object.

```c#
class SampleClass
{
	public SampleClass() //constructor
	{
		//code
	}
}

SampleClass myClass = new SampleClass();
```

## Object Initializer
Used to initialize type objects without evoking a constructor for the type.

```c#
class SampleClass
{
	public int SampleProperty
	{get;set;}
	public int SampleProperty2
	{get;set;}
}

SampleClass myClass = new SampleClass()
{
	SampleProperty = 100, SampleProperty2 = "Sample String Content"
};
```