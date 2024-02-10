[[OOP]]
---
# Interface

Represents a contract. It contains definitions for a group of related functionalities that a `class` or `struct` can implement.

It is a `custom type reference`.

```csharp
interface ISampleInterface {
	void SampleMethod();
}
```

```csharp
class SampleClass : ISampleInterface {
	public void SampleMethod() {
		//implementation
	}
}
```

## Interface Properties
- must implement all its members,
- cannot be instantiated directly
- can contain:
	- events
	- indexers
	- methods
	- properties
- contains no implementation
- a `class` or `struct` can implement multiple `interfaces`

```csharp
public interface IShape {
    double GetArea();
}

public class Circle : IShape {
    public double Radius { get; set; }
    public double GetArea() {
        return Math.PI * Radius * Radius;
    }
}

public class Square : IShape {
    public double Side { get; set; }
    public double GetArea() {
        return Side * Side;
    }
}

// Usage:
IShape circle = new Circle { Radius = 5 };
IShape square = new Square { Side = 4 };
Console.WriteLine(circle.GetArea()); // Output: 78.54...
Console.WriteLine(square.GetArea()); // Output: 16

```

Here, `IShape` serves as an interface defining a contract for classes that implement it, enabling polymorphic behavior through `GetArea()` method implementation in `Circle` and `Square` classes.
