[[Bootcamp Notes]]
---

# Unit Tests
## MS Test

Use `MS Test` Project Template in VS.

It is better to create a `Using.cs` with the line

`global using Microsoft.VisualStudio.TestTools.UnitTesting;` in order to use the test globally.

Follow templates and ensure that main method is testable.

In the test method, declare the object from main, then pass the variables

**Main Method**

```csharp
using System;
namespace Demo
{
    public class Calculator
    {
        public double Addition(double operand1, double operand2) => operand1 + operand2;
        public double Subtraction(double operand1, double operand2) => operand1 - operand2;
        public double Multiplication(double operand1, double operand2) => operand1 * operand2;
        public double Division(double operand1, double operand2) => (operand2 != 0) ? operand1 / operand2 : throw new DivideByZeroException();
    }
}

```

Sample calculator program for testing

**Test Method**

```csharp
namespace Demo {
	[TestClass]
	public class CalculatorTest {
		[TestMethod]
		public void AdditionTest() {
			Calculator sut = new(); // create instance object
			
			double operand1 = 1;
			double operant2 = 2;
			double expected = 3;
			double actual
			
			actual = sut.Addition(operand1, operand2) // invoke Addition() with args
			
			Assert.AreEqual(expected, actual); // compare the actual result to the expected result
		}
	}
}
```

## NUnit Test Projects and NUnit NUget Packages
