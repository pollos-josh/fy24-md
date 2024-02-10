[[OOP]]
---

# Type Conversions

Converting one data to another.

## Implicit Conversions

No syntax required as this is quite safe and no data is lost.

This is allowed in converting small types to larger types.

```csharp
int intVariable = 100;
long longVariable = intVariable;
```

## Explicit Conversions

Require a cast operator.

Used when information might be lost, or the conversion might not succeed. Also when converting data to a less precise type.

```csharp
long longVar = 100;
int intVar = (int)longVariable;
```

# Is and As
## Is

Evaluates type compatibility.

```csharp
if (object is SomeType) {
	// do something
}
```

## As

Functions like a cast operator. Returns `null` instead of throwing an exception if conversion is not possible.

```csharp
BaseClass baseObject = new BaseClass();

//Returns null
DerivedClass derivedObject = baseObject as DerivedClass;

if (derivedObject != null){
	derivedObject.SampleDerivedMethod();
	//...
}
```

# Boxing and Unboxing

*Boxing* implicit conversion of a value type to the type object.

```csharp
int myInteger = 100;

//Boxing copies the value of myInteger to myObject
object myObject = myInteger;
```

*Unboxing* explicit conversion from value object to value type.

```csharp
object myObject = 100;

//Boxing copies the value of myObject to myInteger 
int myInteger = (int)myObject;
```
