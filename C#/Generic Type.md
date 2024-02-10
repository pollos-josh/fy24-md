[[OOP]]
---
# Generics

Defines `methods`, `classes`, and `interfaces` with the placeholder. It allows `type` to be a param to `methods`, etc.

The specification of one or more types are deferred until the method is declared and instantiated.

```csharp
public class GenericClass<T> {
	public T GenericField;

	public T GenericMethod(T parameter) {
	}
}
```

```csharp
GenericClass<int> genericObject = new GenericClass<int>();
```

This is useful for when you want to store data in a single `class` without regard for its type.

```csharp
public class GenericStack<T>
{
    private T[] elements;
    private int top;

    public GenericStack(int capacity)
    {
        elements = new T[capacity];
        top = -1;
    }

    public void Push(T item)
    {
        if (top == elements.Length - 1)
        {
            Console.WriteLine("Stack overflow");
            return;
        }

        elements[++top] = item;
    }

    public T Pop()
    {
        if (top == -1)
        {
            Console.WriteLine("Stack underflow");
            return default(T);
        }

        return elements[top--];
    }

    public void PrintStack()
    {
        if (top == -1)
        {
            Console.WriteLine("Stack is empty");
            return;
        }

        Console.WriteLine("Stack elements:");
        for (int i = top; i >= 0; i--)
        {
            Console.WriteLine(elements[i]);
        }
    }
}
```

---
# Generic Collections

```csharp
//List<T>
List<int> intList = new intList<int>();
intList.Add(10);
```

```csharp
//Dictionary<TKey, TValue>
Dictionary<string, int> valuePairs = new Dictionary<string, int>();
valuePairs.Add("hello", 10);
```
