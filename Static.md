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