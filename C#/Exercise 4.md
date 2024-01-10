[[Bootcamp Notes]]
---

# Parallelogram

Trying to think through an algorithm for the parallelogram.
The sample output is more of a rhombus, with equal length (in `*`) in all sides.

The user is only allowed to give an input for the base, so using that, we can calculate how many spaces we need to print before the asterisks.

```csharp
for (int i = base - 1; i >=0; i--) { // this one wraps the whole loop.
	for (int j = 0; j < base - i + 1; j++) {
		Console.Write(" "); // print the leading spaces
	}

	for (int x = 0; x < base + 1; x++) {
		Console.Write("*"); // print asterisks
	}
	Console.WriteLine();
}
```

# WORKING!! FIRST TRY 