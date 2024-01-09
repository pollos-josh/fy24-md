[[ADO .NET]]
---
##### might have to pray to [[God]] for this one.

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
    
>2. **Inline Usage:** Lambdas are handy when you need to pass small pieces of functionality as arguments to methods. Instead of defining a separate method or anonymous method, lambdas allow you to create the function inline, right where it's needed.
    
>3. **Ease of Use with LINQ and Functional Programming:** Lambdas work seamlessly with LINQ queries and functional programming paradigms. They enable the use of higher-order functions like `Where`, `Select`, `OrderBy`, and others, making code more declarative and functional.
    
>4. **Avoiding Named Method Overload:** For one-time or limited-use functions, using a lambda eliminates the need to create separate named methods. This prevents method overload and cluttering the codebase with functions that might have a single or limited use.
    
>5. **Closure and Capturing Variables:** Lambdas can capture variables from their enclosing scope, making it easy to work with variables in the context they are created. This feature, called closure, allows lambdas to use variables from the surrounding code without passing them explicitly.
    
>6. **Functional Composition:** Lambdas facilitate functional composition, enabling the creation of complex operations by combining simpler functions. This encourages a more modular and compositional approach to coding.



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

```csharp
var cust
```