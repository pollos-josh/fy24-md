[[Bootcamp Notes]]
---

Reverse an int without leading zeros. 
*Failed this one*

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
	        int[] digits = GetDigitsArray(n); // push individual digits into an array

	        int[] results = new int[digits.Length]; // results array
	        int resultIndex = 0; // Index to keep track of the result array
	
	        bool leadingZeroFound = false; // Flag to track leading zeros
	
	        for (int j = digits.Length - 1; j >= 0; j--) // initialize pointer to last digit
	        {
	            if (digits[j] == 0 && !leadingZeroFound)
	            {
	                continue; // Skip leading zeros
	            }
	
	            leadingZeroFound = true; // Set the flag once a non-zero digit is found
	
	            // push digits[j] into the new array results[] 
	            results[resultIndex++] = digits[j];
	        }
	
	        // Construct the reversed integer directly
	        int finalResults = 0;
	        for (int i = 0; i < resultIndex; i++)
	        {
	            finalResults = finalResults * 10 + results[i];
	        }
	        return finalResults;
	    }
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


# What went wrong...? 

I originally pushed this as a class library. This is wrong.
Make a class `Program` with `public void Main()` then call the `Solution` class.

There is also something wrong with the logic here
```csharp

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
}
```

Maybe there's something wrong with `GetValidIntegerInput()`. I modified it a bit for this project.
```csharp
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

```

# Fixed code
Turns out, there were duplicated `Console.ReadLine()` and `WriteLine()` methods that were messing with the loop input. The main issue was with `Main` passing on the wrong variables and `GetValidIntegerInput` having `int prompt`.
```csharp
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
///...
}
```

```csharp
static int GetValidIntegerInput(int prompt)
{
	int result;
	bool isValidInput = false;
```

`GetValidIntegerInput` is supposed to get `string prompt` from `Main`. It's supposed to print a string to prompt the user to input a variable. This got broken in transitioning from a *ConsoleApp* to a *ClassLibrary*.

Finally, parsing an `int` from a `string` can lead to unexpected results, leading to duplicated `array` elements e.g.
```
N = 250
result = 55
```

It's better to construct 
Here is the corrected code:
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

            //Console.WriteLine("Enter a positive integer:");
            int userInput = Solution.GetValidIntegerInput("Enter a positive integer: ");

            Console.WriteLine("The reversed integer is: " + solution.Method(userInput));
            Console.ReadKey(); // To prevent the console window from closing immediately
        }
    }

	public class Solution
	{
	    public int Method(int N)
	    {
            int[] digits = GetDigitsArray(N); // push individual digits into an array

	        int[] results = new int[digits.Length]; // results array
	        int resultIndex = 0; // Index to keep track of the result array
	
	        bool leadingZeroFound = false; // Flag to track leading zeros
	
	        for (int j = digits.Length - 1; j >= 0; j--) // initialize pointer to last digit
	        {
	            if (digits[j] == 0 && !leadingZeroFound)
	            {
	                continue; // Skip leading zeros
	            }
	
	            leadingZeroFound = true; // Set the flag once a non-zero digit is found
	
	            // push digits[j] into the new array results[] 
	            results[resultIndex++] = digits[j];
	        }
	
	        // Construct the reversed integer directly
	        int finalResults = 0;
	        for (int i = 0; i < resultIndex; i++)
	        {
	            finalResults = finalResults * 10 + results[i];
	        }
	        return finalResults;
	    }
	 

        // Function to validate and parse integer input 
        public static int GetValidIntegerInput(string prompt)
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

        public static int[] GetDigitsArray(int number)
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