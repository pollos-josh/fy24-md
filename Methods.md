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
namespace Demo
{
    using MyNamespace;
    class Program
    {
        static void Main(string[] args)
        {
            SampleClass sampleClass = new SampleClass();
            sampleClass.SampleMethod(); // calls method in different class

            MethodA();

            MyClass.MyMethod(); //full syntax: MyNamespace.MyClass.MyMethod()
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