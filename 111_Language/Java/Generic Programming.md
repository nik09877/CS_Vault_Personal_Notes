# Why Generic Programming ?

- Generic programming means writing code that can be reused for objects of different types.

#### Example:
```Java
var files = new ArrayList<String>();
ArrayList<String>files = new ArrayList<>(); //diamond syntax
```

# Defining a simple Generic class
- Generic class acts like a factory for ordinary classes.
- A Generic class is a class with one or more type variables.

#### Example:
```Java
public class Pair<T> // Pair<T,U> could also have been defined. 
{
	private T first;
	private T second;
	public pair() { first = null; second = null; }
	public pair(T first, T second) { this.first = first; this.second = second}
	public T getFirst() { return first; }
	public T getSecond() { return second; }
	public void setFirst(T newVal) { first = newVal; }
	public void setSecond(T newVal) { second = newVal; }
}

public class Main
{
	public static void main(String[] args)
	{
		var p = new Pair<int>(1,2);
		System.out.println(p.getFirst() + " " + p.getSecond());
	}
}
```
#### Note:
- The Java library uses the variable **E** for the element **type of a collection**, **K** and **V** for **key and value** types of a table, and **T** (and the neighboring letters U and S, if necessary) for **any type at all.**

# Generic Methods

```Java
class ArrayAlg
{
	public static <T> T getMiddle(T... a)
	{
		return a[a.length/2];
	}
}
```

- You can define generic methods both inside ordinary and generic classes;
- When you call a generic method, you can place the actual types, enclosed in angle brackets, before the method name.
```Java
String middle = ArrayAlg.<String>getMiddle("John","Q.","public");
```
- In most cases you can omit the `<T>` type parameter when calling a method.
- But it doesn't work in this case :
```Java
double middle = ArrayAlg.getMiddle(3.14,12,0);
```
- Here the compiler auto boxed the parameter into a Double and two Integer objects and tried to find a common super type of these classes.
- It found 2 : Number and Comparable interface, which in itself is a generic type.
- In this case we need to write all parameters as double values.

# Bounds for type variables
- Sometimes a class or a method needs to place restrictions on type variables.
### The Problem
```Java
class ArrayAlg
{
	public static <T> T min(T[] a)
	{
		if(a == null || a.length == 0)
			return null;
		T smallest = a[0];
		for(int i=1;i<a.length;i++)
		{
			if(smallest.compareTo(a[i]) > 0)
				smallest = a[i];
		}
		return smallest;
	}
}
```
- Here `smallest` has type **T**, which means it could be an object of an arbitrary class.
- How do we know that the class implements the `Comparable` interface which has a single method `compareTo` ?

### The solution
- We need to give a bound for the type variable T:

```Java
public class <T extends Comparable> T min(T[] a)
```

#### Why use extends keyword instead of implements ?
- Both **T** and the **bounding type** can be either a class or an interface.
- `extends` is used to express that T should be a subtype of the bounding type.

### Note
- A type can have multiple bounds which are separated by `&` operator.

```Java
<T extends Comparable & Serializable>
```

- There can be at most **1 class** as the bounding type and it must be declared first in the bounds list.

# Generic Code and Virtual Machine
- There are no generics in the virtual machine, only ordinary classes and methods.
- All type parameters are replaced by their bounds or `Object`.
- Bridge methods are synthesized to preserve polymorphism.
- Casts are inserted as necessary to preserve type safety.
# Restrictions and Limitations

#### 1. You can't use primitives as type parameter:
- Thus, there is no Pair `<double`, only Pair `<Double>`.
- The reason is, of course ***type erasure***, due to which all type parameters are replaced by their bounds.
#### 2. Runtime type inquiry only works with Raw types
- Objects in the virtual machine always have a specific non generic type. Therefore, all type inquiries yield only the raw type.
```Java
if(a instanceof Pair<String>) //ERROR
if(a instanceof Pair<T>) //ERROR
Pair<String> p - (Pair<String>) a; //warning--can only test that a is a pair
```
- In the same spirit, the `getClass` method always returns the raw type.
```Java
Pair<String>stringPair = . . .;
Pair<Employee> employeePair = . . .
```


