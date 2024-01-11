[[Bootcamp Notes]]
---

Reverse an int without leading zeros. Failed this one
```csharp
using System;
using System.Linq;

namespace Exercise_5
{
    class Program
    {
        static void Main(string[] args)
        {
            // You can use the Solution class here
            Solution solution = new Solution();

            // Example usage:
            Console.WriteLine("Enter a positive integer:");
            int userInput = int.Parse(Console.ReadLine());

            int result = solution.Method(userInput); 
            Console.ReadKey(); // To prevent the console window from closing immediately
        }
    }

    public class Solution
    {
        public int Method(int N)
        {
            int n = GetValidIntegerInput(N); // parse input
            int[] digits = GetDigitsArray(n);
            // push individual digits into an array
            int[] results = new int[digits.Length];

            bool leadingZeroFound = false; // Flag to track leading zeros

            for (int i = 0; i < digits.Length; i++) // initialize pointer to first digit
            {
                for (int j = digits.Length - 1; j > 0; j--) // initialize pointer to last digit
                {
                    if (digits[j] == 0 && !leadingZeroFound)
                    {
                        continue; // Skip leading zeros
                    }

                    leadingZeroFound = true; // Set the flag once a non-zero digit is found

                    // push digits[j] into the new array results[] 
                    results[i] = digits[j];
                    break; // Break to exit the inner loop after pushing a non-zero digit
                }
            }
            string concatString = string.Concat(results); // Concatenate the array into a string
            int finalResults = int.Parse(concatString); // Parse the string into an integer

            Console.WriteLine($"Is Decimal Reverse?: {!leadingZeroFound}");

            return finalResults;
        }

        // Function to validate and parse integer input 
        static int GetValidIntegerInput(int prompt)
        {
            int result;
            bool isValidInput = false;

            do
            {
                Console.WriteLine(prompt);
                string input = Console.ReadLine();

                if (!int.TryParse(input, out result) || result < 0 || result > 1000000000)
                {
                    Console.WriteLine("Invalid input. Please enter a valid positive integer less than 1,000,000,000.");
                }
                else
                {
                    isValidInput = true;
                }
            } while (!isValidInput); // keep throwing errors and asking for input until the input is valid

            return result;
        }

        static int[] GetDigitsArray(int number)
        {
            // Convert the number to a string to easily extract individual digits
            string numberString = number.ToString();

            // Create an array to store individual digits
            int[] digits = new int[numberString.Length];

            // Iterate through each character in the string and convert it to an integer
            for (int i = 0; i < numberString.Length; i++)
            {
                digits[i] = int.Parse(numberString[i].ToString());
            }

            return digits;
        }
    }
}

```


# Takeaways
I originally pushed this as a class library. This is wrong.
Make a class `Program` with `public void Main()` then call the ``