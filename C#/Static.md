[[Classes]]
---
# Static

Members of the class shared by all instances of a class.

```c#
static class SampleClass
{
	public static string SampleField = "Sample String";
}
```

To access the static member, use name of the class

```c#
Console.WriteLine(SampleClass.SampleField);
```

Static classes has static members only and cannot be instantiated. Also can't access non-static members.

Static members can't be called by the instantiated variable. You must use its *ClassName*. Same with *const* variables.

```csharp
class Program {
	public static void Main(string[] args) {
		Car car = new Car();
		Car.Maker = "Nissan";      //must use ClassName not varName

		///car 1
		car.model = "Terra"
		car.yearBuilt = "1998";
		car.Maker = ""; //error
		///car 1

		///car 2
		Car car2 = new Car(); // create a new Car object 'car2'
		car2.model = "GTR Skyline";
		car2.yearBuilt = "2005";
		 ///car 2
	}

}

class Car() {
	public const int Milage = 0;
	public static string? maker {get;set;}
	public string? yearBuilt {get;set;}
	public string? model {get;set;}
}
```

Basically *static* members edit the default for a class, changing the variable at a blueprint level.

*Note: Don't make it static if values have to be unique.*
