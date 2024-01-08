[[Bootcamp Notes]]
---

## Inverted Equilateral Triangle
This is just a simple console program.
```csharp
using System;

namespace Exercise_3
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
                else if (result > 20)
                    Console.WriteLine("Invalid input. Please enter a valid positive integer less than or equal to 20.");
                else
                {
                    isValidInput = true;
                }
            } while (!isValidInput); // keep throwing errors and asking for input until the input is valid

            return result;
        }

        // Function to display an inverted triangle
        static void DisplayTriangle(int height)
        {
            for (int i = height - 1; i >= 0; i--)
            {
                for (int j = 0; j < height - i + 1; j++)
                {
                    Console.Write(" "); // print leading spaces
                }

                for (int x = 0; x < i * 2 - 1; x++)
                {
                    Console.Write("*"); // print asterisks
                }
                Console.WriteLine(); // Move to the next line for the next row of the triangle
            }
        }
    } 
}
```


## Trick
The trick here is the `do-while` validation for `GetValidInteger()` method.
```csharp
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
                else if (result > 20)
                    Console.WriteLine("Invalid input. Please enter a valid positive integer less than or equal to 20.");
                else
                {
                    isValidInput = true;
                }
            } while (!isValidInput); // keep throwing errors and asking for input until the input is valid

            return result;
        }
```
## Inverted Triangle Snippet
Neat little function. Takes the `height` of the triangle and prints leading spaces using it.
This makes the whole equilateral thing.
```csharp
 static void DisplayTriangle(int height)
        {
            for (int i = height - 1; i >= 0; i--)
            {
                for (int j = 0; j < height - i + 1; j++)
                {
                    Console.Write(" "); // print leading spaces
                }

                for (int x = 0; x < i * 2 - 1; x++)
                {
                    Console.Write("*"); // print asterisks
                }
                Console.WriteLine(); // Move to the next line for the next row of the triangle
            }
        }
```