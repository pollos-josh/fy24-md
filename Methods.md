[[Classes]]
---
C# Functions containing a series of statements or code to perform.

```csharp
class SampleClass 
{
	public void Method()
	{
		//code here
	}
}
```

 ```csharp
namespace Demo
{
    class Program
    {
        static void Main(string[] args)
        {
            SampleClass sampleClass = new SampleClass();
            sampleClass.SampleMethod(); 
            // calls method in different class

            MethodA(); 
            //calls method in same class

            MyNamespace.MyClass.MyMethod(); 
			//calls method in different namespace
        }

        static void MethodA()
        {
            Console.WriteLine("MethodA");
        }
    }

    class SampleClass
    {
        public void SampleMethod() 
        {
            Console.WriteLine("Sample Method");
        }
    }
}

namespace MyNamespace
{
    class MyClass()
    {
        public static void MyMethod()
        {
            Console.WriteLine("Foreign Namespace Method");
        }
    }
}
```  
*Calling methods in other classes.*
*Initialize class in Main() then declare constructor. Then call method.*

*Call method from other namespace.
Full syntax is MyNamespace.MyClass.MyMethod()*
## Methods are declared by:
- Methods can be *public* or *private*.
- Optional modifiers include: *abstract* or *sealed*.
- The *return* value.
- Name of the method.
- Any method parameters.

## Parameters
Method parameters are enclosed in parenthesis. Empty parenthesis mean that the method doesn't require params.
```csharp
public void Main(){
	//code
}
public void SampleMethod(int parameter, string param2){
	//code
}
```

## Arguments
When calling methods that require parameters, we must provide arguments to satisfy it.
```csharp
public void Main(){
	SampleMethod(1000, "hello");
}

public void SampleMethod(int param1, string param2){
	//code
}
```

## Method Overloading
Different implementations of one method within a class.
```csharp
class MainClass {
    public void Method() {
        Console.WriteLine("Empty overload..");
    }

    public void Method(int param1) {
        Console.WriteLine($"Overload 1: {param1}");
    }

    public void Method(int param1, string param2) {
        Console.WriteLine($"Overload 2: {param1}, {param2}");
    }
}
```
*note: $ enables easy concatenating of strings and variables, with variables in {curly braces}*👍 

*note note: it is also wise to add summary/documentation to overloaded methods to prevent sphagetti*
```csharp
class MainClass {
	public void Method() {
		/// <summary>
		/// Default non-overload. No params
		/// </summary>
        Console.WriteLine("Empty overload..");
    }

    public void Method(int param1) {
		/// <summary>
		/// Overload 1. Enter int.
		/// </summary>        
        Console.WriteLine($"Overload 1: {param1}");
	}
	
     public void Method(int param1, string param2) {		
		/// <summary>
		/// Overload 2. Requires int and param. Concatenates param1 and 2
		/// </summary>        
        Console.WriteLine($"Overload 2: {param1}, {param2}");
    }
}
```

## Comments
This applies to the entirety of coding but in C#, pressing `///` will automatically add an XML summary function.

```csharp
/// <summary>
/// Description of method/class/struct/function.
/// </summary>
/// <param name="parameter">parameter descriptionargs</param>
/// <returns>Description of what the function returns</returns>

```