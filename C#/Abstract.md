[[OOP]]
---

# Abstract

**Definition:** An abstract class is a class that cannot be instantiated on its own and may contain abstract methods (methods without implementation) as well as concrete methods (methods with implementation).

```csharp
// Abstract class representing a Shape
public abstract class Shape
{
    // Abstract method for calculating area, to be implemented by derived classes
    public abstract double CalculateArea();
    
    // Concrete method within the abstract class
    public void PrintArea()
    {
        Console.WriteLine($"Area: {CalculateArea()}");
    }
}

// Derived class Circle inheriting from Shape
public class Circle : Shape
{
    public double Radius { get; set; }

    // Implementation of abstract method CalculateArea for Circle
    public override double CalculateArea()
    {
        return Math.PI * Radius * Radius;
    }
}

// Derived class Square inheriting from Shape
public class Square : Shape
{
    public double Side { get; set; }

    // Implementation of abstract method CalculateArea for Square
    public override double CalculateArea()
    {
        return Side * Side;
    }
}

class Program
{
    static void Main()
    {
        // Creating instances of Circle and Square
        Circle circle = new Circle { Radius = 5 };
        Square square = new Square { Side = 4 };

        // Calling methods of the abstract class
        circle.PrintArea(); // Output: Area: 78.53981633974483
        square.PrintArea(); // Output: Area: 16
    }
}
```

- `Shape` is an abstract class with an abstract method `CalculateArea()` representing the calculation of the area for any shape. It also has a concrete method `PrintArea()` that uses the abstract method `CalculateArea()` to print the area.
    
- `Circle` and `Square` are concrete classes that inherit from `Shape` and provide their own implementations of the `CalculateArea()` method based on their specific shapes.
    
- In the `Main()` method, instances of `Circle` and `Square` are created and their `PrintArea()` methods are called, demonstrating the usage of the abstract class and its concrete implementations.

This setup allows for a shared structure among different shapes while allowing each shape to provide its specific implementation of the area calculation method.
