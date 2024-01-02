[[Classes]]
---
C# Functions. Contains a series of statements or code to perform.

```c#
class SampleClass 
{
	public void Method()
	{
		//code here
	}
}
```

 ```c#
class SampleClass
{
	public SampleClass() //constructor
	{
		static void Main()
		{
			MethodA();
			
			NewClass newClass = new NewClass(); //constructor
			newClass.SampleMethod();
		}

		static void MethodA()
		{
			Console.WriteLine("MethodA");
		}
	}
}

class NewClass
{
	public static void SampleMethod() //constructor
	{
		Console.WriteLine("NewClass Sample Method");
	}
}
```  
*Calling methods in other classes.*
*Initialize class in Main() then declare constructor. Then call method.*
## Methods are declared by:
- Methods can be *public* or *private*.
- Optional modifiers include: *abstract* or *sealed*.
- The *return* value.
- Name of the method.
- Any method parameters.