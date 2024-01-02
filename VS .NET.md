# .NET Core
Cross platform open-source dev environment for building different types of applications.
Allows for building on Windows, Linux, and MacOS.

# .NET Framework
Only for Windows applications.

# Common Language Runtime
- Core component of .NET Core. Manages memory, security, execution, etc.

## Visual Studio
	.NET 8
		CLR
## Managed Code
Refers to code that benefits from runtime services and management provided by CLR.

## Unmanaged Code
Refers to code that is not executed and managed by CLR. Typically consists of languages that do not target CLR or code that is directly executed by the OS.


----

# Data Types
1. **Value Types** - store data directly in memory. *INT, CHAR, BOOL, UDS*
2. **Reference Types** - stores a reference of location in memory -> actual data.

## Built-in Types
- Also known as *primitive types*. Predefined types by .NET framework.
	- sbyte
	- byte
	- short
	- ushort
	- int
	- uint
	- long
	- ulong
	- char
	- float
	- double
	- decimal
	- bool
	- object
	- string



## Custom Types
- User defined data types.

```C#
class SampleClass {
	//class members go here
}
```

```C#
class SampleStruct {
	//structure members go here
}
```

## Variables
- Used to store and manipulate data.

```c#
int age;
string firstName;
double price = 50;
bool isComplete;
float num = 123.40f
```

## Implicit Data
```C#
var implicitly1 = 100;
var implicitly2 = "abc";
var implicitly3 = true;
```
*soft initialized variable. must be initialized*

## Nullable Type
Can accept null values

```c#
Nullable<int> variable = 10;
bool? = null;
```

## Namespaces
```C#
System.Console.WriteLine("HELLO WORLD!");
using System;
...
	Console.WriteLine("Hello World!");
```

```c#
namespace MyNamespace {
	class Program {
		MyNamespace2.Program Program2;
	}
}

namespace MyNamespace2 {
	class Program {
		static void Main(string[] args) {
		// code
		}
	}
}
```

```
```

## Structures
suitable for representing values with small mem. requirments.
```c#
struct Currency {
	// fields, properties, methods, and events
}
```