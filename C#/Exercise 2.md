[[Bootcamp Notes]]
---

## Inverted Isosceles Triangle
```csharp
using System;

namespace Exercise_2
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int height = GetValidIntegerInput("Enter the height of the triangle: ");
            DisplayTriangle(height);
			Console.ReadLine();
        }

        // Function to validate and parse integer input
        static int GetValidIntegerInput(string prompt)
        {
            int result;
            bool isValidInput = false;

            do
            {
                Console.WriteLine(prompt);
                string input = Console.ReadLine();

                if (!int.TryParse(input, out result) || result <= 0)
                {
                    Console.WriteLine("Invalid input. Please enter a valid positive integer.");
                }
                else
                {
                    isValidInput = true;
                }
            } while (!isValidInput);
			return result;
        }

        // Function to display a triangle
        static void displaytriangle(int height)
        {
            for (int i = 1; i <= height; i++)
            {
                for (int j = 1; j <= i; j++)
                {
                    console.write("*");
                }
                console.writeline(); // move to the next line for the next row of the triangle
            }
        }
    }
}
```

## Inverted Triangle Snippet
```csharp
static void displaytriangle(int height) {
	for (int i = 1; i <= height; i++)
	{
		for (int j = 1; j <= i; j++)
		{
			console.write("*");
		}
		console.writeline(); // move to the next line for the next row of the triangle
	}
}
```