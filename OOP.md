[[Bootcamp Notes]]
---
# Object Oriented Programming
## Abstraction
Handles complexity by hiding unnecessary complex logic from the user. 
Enables the user to implement more complex actions on top of the code without
needing to think about the underlying logic.

```csharp
public class CoffeeMachine {
    private Map<CoffeeSelection, CoffeeBean> beans;

    public CoffeeMachine(Map<CoffeeSelection, CoffeeBean> beans) { 
         this.beans = beans
    }

    public Coffee brewCoffee(CoffeeSelection selection) throws CoffeeException {
        Coffee coffee = new Coffee();
        System.out.println(“Making coffee ...”);
        return coffee;
    }
}
```

## Encapsulation
The first pillar of OOP. It means groups of related properties, methods, etc. are treated as single objects or units.
## Inheritance 
The second pillar. Enables you to reuse, extend, and modify the behavior of pre-defined
classes with other classes.

### Protected
Makes a class accessible within a class and by derived class instances. Declared with `protected` keyword.
```csharp
public class BaseClass {
	protected void SampleMethod() {
	 // code
	}
}

public class DerivedClass : BaseClass {
	SampleMethod(); //successfull call
}

public class NewClass {
	SampleMethod(); //error: inaccessible
}
```

## Polymorphism
Derived classes inherits all properties, fields, methods, etc. from a base class.
```csharp
public class BaseClass {
	new void SampleMethod(){
		//code
	}
	new virtual void SampleMethod() { //code that allows for overriding
		//code
	}
}

public class DerivedClass : BaseClass {
	SampleMethod();
	public new void SampleMethod() { //replace method behavior
		//new code
	} 
	public override virtual SampleMethod() { //override a virtual method
		//new code
	}
}
```