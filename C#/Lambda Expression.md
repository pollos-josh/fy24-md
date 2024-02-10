[[ADO .NET]]
---
##### Might Have to Pray to [[God]] for This One.

# Lambda Expressions

`=>` allows attaching anonymous methods that can contain expressions and statements.

```csharp
MyDelegate myDelegate = new MyDelegate(
	(int parameter1, int parameter2) => // lambda expression
	{
		return parameter1 + parameter2;
	}); //this is same as Addition()
 ```

## Advantages

*from GPT*

> 1. **Conciseness and Readability:** Lambdas are concise, allowing you to define functions in a compact and readable way. This brevity makes code more expressive and easier to understand, especially for short and simple operations.
> 
> 2. **Inline Usage:** Lambdas are handy when you need to pass small pieces of functionality as arguments to methods. Instead of defining a separate method or anonymous method, lambdas allow you to create the function inline, right where it's needed.
> 
> 3. **Ease of Use with LINQ and Functional Programming:** Lambdas work seamlessly with LINQ queries and functional programming paradigms. They enable the use of higher-order functions like `Where`, `Select`, `OrderBy`, and others, making code more declarative and functional.
> 
> 4. **Avoiding Named Method Overload:** For one-time or limited-use functions, using a lambda eliminates the need to create separate named methods. This prevents method overload and cluttering the codebase with functions that might have a single or limited use.
> 
> 5. **Closure and Capturing Variables:** Lambdas can capture variables from their enclosing scope, making it easy to work with variables in the context they are created. This feature, called closure, allows lambdas to use variables from the surrounding code without passing them explicitly.
> 
> 6. **Functional Composition:** Lambdas facilitate functional composition, enabling the creation of complex operations by combining simpler functions. This encourages a more modular and compositional approach to coding.

## LINQ

Language Integrated Queries are higher level statements enabling SQL-like syntax 

```csharp
// sample data class
public class Person {
    public string Name { get; set; }
    public int Age { get; set; }
}

// insert sample data
List<Person> people = new List<Person>{
    new Person { Name = "Alice", Age = 30 },
    new Person { Name = "Jason", Age = 10 },
    new Person { Name = "Schlatt", Age = 75 }
};

static void Main(string[] args) {
    IEnumerable<Person> persons = // LINQ statement to get sample data
		from person in people
        select person;

    foreach (Person person in persons) {
        Console.WriteLine("Name: {0}, Age: {1}", person.Name, person.Age);
    }
}
```

### Sample LINQ Statements

```csharp
 //sample LINQ statements
var olderThan25 = people.Where(person => person.Age > 25);
var namesOnly = people.Select(person => person.Name);
var sortedByAge = people.OrderBy(person => person.Age);

var namesOfOlderThan25Sorted = people
    .Where(person => person.Age > 25)
    .OrderBy(person => person.Name)
    .Select(person => person.Name);
```

A more direct syntax to call LINQ operator methods, and passing lambda expressions as parameters

```csharp
IQueryable<Customer> custQuery = dbCustomers.Where(Cust => cust.City == 'Manila').Select(cust => cust);
```

**Customer list**

```csharp
private static IEnumerable<Customer> customers = new List<Customer>
{
	new Customer{ CustomerId = 1, FirstName = "Emma", LastName = "Lowton", Age= 23, Email = "emma.lowton@avanade.com", Address ="5030 Blue Ridge Dr. Burbank", Active = true },
	new Customer{ CustomerId = 2, FirstName = "Allen", LastName = "Brewer", Age = 30, Email = "allen.brewer@avanade.com", Address ="5375 Clearland Circle Seattle", Active = true },
	new Customer{ CustomerId = 3, FirstName = "William", LastName = "Bowman", Age = 25, Email = "wiliam.bowman@avanade.com", Address ="9537 Ridgewood Drive", Active = false },
	new Customer{ CustomerId = 4, FirstName = "Burton", LastName = "Calvin", Age = 36, Email = "burton.calvin@avanade.com", Address ="6578 Woodhaven Ln. Everett", Active = true },
	new Customer{ CustomerId = 5, FirstName = "Royce", LastName = "Freeland", Age = 21, Email = "royce.freeland@avanade.com", Address ="9784 Mt Etna Drive Edmons Renton", Active = true }
};

```

## LINQ and SQL

```csharp
var customerLastNames = customers.Select(customer => customer.LastName); 
```

*This pushes `customer.LastName` from `IEnumerable<Customer> customers` using `Select`.*

 It's easier to think about this as a longer SQL statement. Notice that `SELECT CustomerName FROM Customers` is similar to the first code block, just rearranged. 

Another implementation is:

 ```csharp
var selectedCustomers = customer.Select(customer => customer);

foreach (Customer selectedCustomer in selectedCustomers) {
	Console.WriteLine("Customer Name: {0} {1}", selectedCustomer.FirstName, selectedCustomer.LastName);
}
```

*Return the whole `customer` object with `FirstName` and `LastName`.*

### Headtrauma and Nosebleed

We can start going crazy from here with `Where`. Similar to `WHERE` in SQL, it's an additional condition statement for filtering.

```csharp
static void Main(string[] args) {
	var selectedCustomers =
		customers
		.Where(customer => customer.Active == true)
		.Select(customer => new { customer.FirstName, customer.LastName }); // selects customer name where `Active` is equal to true

	// loop through results
	foreach (var selectedCustomer in selectedCustomers) {
		Console.WriteLine("Customer Name: {0} {1}", selectedCustomer.FirstName, selectedCustomer.LastName);
	}

	Console.Read();
}
```

## LINQ Aggregators

Similar to SQL syntax, LINQ also has aggregators `Distinct`, `Count`

```csharp
static void Main(string[] args) {
	int[] numbers = { 2, 2, 3, 4, 5, 5, 6, 6, 7, 7 }

	int distinct = numbers.Distinct().Count();

	Console.WriteLine("There are {0} unique numbers.", count); // this prints the first method in int distinct

	IEnumerable<int> distinctNumbers = numbers.Distinct(); // pushes distinct numbers into a List called distinctNumbers

	foreach (var distinctNumber in distinctNumbers) { // loops through each distinct number
		Console.WriteLine(distinctNumber); // and prints it
	}
}
```

Other aggregators like `Sum`, `Min`, `Max`, and `Average` are hardcoded into C#.

```csharp
int minimum = numbers.Min();
int maximum = numbers.Max();
int summation = numbers.Sum();
int average = numbers.Average();
 ```
