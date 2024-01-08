[[Bootcamp Notes]]
---

## Trapezoid
```csharp
using System;


namespace ConsoleApp1
{
    internal class Program
    {
        static void Main(string[] args)
        {
            try
            {
                //input block
                Console.WriteLine("Enter Trapezoid side length: ");
                int side1 = Convert.ToInt32(Console.ReadLine());

                Console.WriteLine("Enter Trapezoid side length: ");
                int side2 = Convert.ToInt32(Console.ReadLine());

                Console.WriteLine("Enter Trapezoid height: ");
                int side3 = Convert.ToInt32(Console.ReadLine());

                Console.WriteLine("Enter Trapezoid base: ");
                int side4 = Convert.ToInt32(Console.ReadLine());
                //input block

                Trapezoid trapezoid = new Trapezoid(); // create new instance of Trapezoid class

                Console.WriteLine("Trapezoid Area: " + trapezoid.getArea(side1, side2, side3, side4)); // call getArea method from Trapezoid class
                Console.WriteLine("Trapezoid Perimeter: " + trapezoid.getPerimeter(side1, side2, side3, side4)); // call getPerimeter method from Trapezoid class
                Console.ReadLine();
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message); // exception handling
                Console.ReadLine();
            }
        }
    }

    public class Trapezoid
    {
        public int getArea(int side1, int side2, int height, int baseLength)
        {
            return ((side1 + side2) / 2) * height;
        }

        public int getPerimeter(int side1, int side2, int side3, int side4)
        {
            return side1 + side2 + side3 + side4;
        }
    }
}
```

- [ ] TODO: Automatically convert input to nearest whole number