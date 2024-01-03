[[Bootcamp Notes]]
---
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
## [[Classes]]
```csharp
class SampleClass {
	//class members go here
}
```

```csharp
class SampleStruct {
	//structure members go here
}
```

## Variables
- Used to store and manipulate data.

```csharp
int age;
string firstName;
double price = 50;
bool isComplete;
float num = 123.40f
```

## Implicit Data
```csharp
var implicitly1 = 100;
var implicitly2 = "abc";
var implicitly3 = true;
```
*soft initialized variable. must be initialized*

## Nullable Type
Can accept null values

```csharp
Nullable<int> variable = 10;
bool? = null;
```

## Namespaces
```csharp
System.Console.WriteLine("HELLO WORLD!");
using System;
...
	Console.WriteLine("Hello World!");
```

```csharp
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

```csharp
using MyNamespace

namespace Demo {
	class Program {
		static void Main(string[] args) {
			//code
		   Program2();
		}
	}
}


namespace MyNamespace {
	class Program2 {
		//code
	}
}
```

## Structures
suitable for representing values with small mem. requirements.
```csharp
namespace Demo {
	class Program {
		static void Main(string[] args) {
			Currency unitedStatesCurrency;
			unitedStatesCurrency.currencyCode = 'USD';
			unitedStatesCurrency.currencySymbol = '$';
		}
	}
}
struct Currency {
	public string currencyCode; //sample field
	public string currencySymbol;
}
```

```csharp
struct Currency {
	private string currencyCode;
	private string currencySymbol;

	public Currency(string code, string symbol){ // constructor
		currencyCode = code;
		currencySymbol = symbol;
	}
}

namespace Demo {
	class Program {
		static void Main(string[], args) {
			 Currency unitedStatesCurrency = new Currency("USD", $);
			 Currency philippineCurrency = new Currency("PHP", ₱);
		}
	}
}
```

## [[Methods]]