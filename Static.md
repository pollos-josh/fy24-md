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

Static members can't be called by the instantiated variable. You must use *ClassName*. Same with *const* variables.
```csharp
class Program {
	public static void Main(string[] args) {
		Car car = new Car();
		car.YearBuilt = "1998";
		car.Maker = ""; //error
		Car.Maker = "Ford";      //must use ClassName not varName

		Console.WriteLine(Car.Milage);
	}

}

class Car() {
	public const int Milage = 0;
	public static string? maker {get;set;}
	public string? yearBuilt {get;set;}
}
```
