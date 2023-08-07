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
### Example :
- ![[Pasted image 20230807125247.png]]

# Generic Code and Virtual Machine
- There are no generics in the virtual machine, only ordinary classes and methods.
- All type parameters are replaced by their bounds or `Object`.
- Bridge methods are synthesized to preserve polymorphism.
- Casts are inserted as necessary to preserve type safety.
### Type Erasure
- Whenever you define a generic type, a corresponding raw type is automatically provided.
- The name of the raw type is simply the name of the generic type, with the type parameters removed. 
- The type variables are erased and replaced by their bounding types (or `Object` for variables without bounds).
- ![[Pasted image 20230807125522.png]]
- The raw type replaces type variables with the first bound, or Object if no bounds are given.
- ![[Pasted image 20230807125645.png]]

### Translating Generic Expressions
- When you program a call to a generic method, the compiler inserts casts when the return type has been erased.
- ![[Pasted image 20230807125921.png]]
### Translating Generic Methods
- ![[Pasted image 20230807130340.png]]
- ![[Pasted image 20230807130835.png]]
- ![[Pasted image 20230807130850.png]]

# Restrictions and Limitations

#### 1. You can't use primitives as type parameter:
- Thus, there is no Pair `<double`, only Pair `<Double>`.
- The reason is, of course ***type erasure***, due to which all type parameters are replaced by their bounds.
#### 2. Runtime type inquiry only works with Raw types
- Objects in the virtual machine always have a specific non generic type. Therefore, all type inquiries yield only the raw type.
```Java
if(a instanceof Pair<String>) //ERROR
if(a instanceof Pair<T>) //ERROR
Pair<String> p = (Pair<String>) a; //warning--can only test that a is a pair
```
- In the same spirit, the `getClass` method always returns the raw type.
```Java
Pair<String>stringPair = . . .;
Pair<Employee> employeePair = . . .;
if (stringPair.getClass() == employeePair.getClass()) // returns true because both return Pair.class
```
#### 3. You can't create arrays of parameterized types

```Java
var table = new Pair<String>[10]; //ERROR
```
- ![[Pasted image 20230807131210.png]]
- Note that only the creation of these arrays is outlawed. You can declare a variable of type `Pair<String>[]`. But you can’t initialize it with a` new Pair<String>[10]`.


##### Note
- You can declare arrays of wildcard types and then cast them
```Java
var table = (Pair<String>[]) new Pair<?>[10];
```
- The result is not safe. If you store a `Pair<Employee>` in table[0] and then call a `String` method on `table[0].getFirst()`, you get a `ClassCastException`.

#### 4. Varargs warning
- Passing instances of a generic type to a method with a variable number of arguments will give us a warning not an error.
```Java

public static void addAll(Collection<T> coll, T... ts)
{
	for (T t : ts) coll.add(t);
}
Collection<Pair<String>> table = . . .;
Pair pair1 = . . .; 
Pair pair2 = . . .; 
addAll(table, pair1, pair2);
```
- You can suppress the warning in one of **two** ways.
	- You can add the annotation `@SuppressWarnings("unchecked")` to the method containing the call to `addAll`.
	- you can annotate the `addAll` method itself with `@SafeVarargs`:
```Java
@SafeVarargs 
public static void addAll(Collection coll, T... ts)
```
- The `@SafeVarargs` can only be used with `constructors` and `methods` that are `static`, `final`, or (as of Java 9) `private`. Any other method could be overridden, making the annotation meaningless.
##### How to create array of generic type using @safeVarargs ?

```Java
@SafeVarargs static E[] array(E... array) { return array; }
// Now you can call
Pair[] table = array(pair1, pair2);
```
- This seems convenient, but there is a hidden danger. The code
```Java
Object[] objarray = table; 
objarray[0] = new Pair();
```
- will run without an `ArrayStoreException` (because the array store only checks the erased type), and you’ll get an exception elsewhere when you work with table[0].

#### 5. You can't instantiate type variable
- You cannot use type variables in an expression such as `new T(. . .)`
- ![[Pasted image 20230807132740.png]]
#### 6. You can't create a Generic array
Just as you cannot instantiate a single generic instance, you cannot instantiate an array. The reasons are different—an array is, after all, filled with `null` values, which would seem safe to construct. But an array also carries a type, which is used to monitor array stores in the virtual machine. That type is erased. For example, consider
```Java
public static <T extends Comparable> T[] minmax(T... a)
{
	T[] mm = new T[2]; //ERROR
	. . . 
}
```
Type erasure would cause this method to always construct an array `Comparable[2]`.
![[Pasted image 20230807132318.png]]
#### 7. Type Variables can't be static
For example, the following clever idea won’t work:

```
public class Singleton<T>
{
	private static T singleInstance; //ERROR
	public static T getSingleInstance() //ERROR
	{
		. . .
	}
}
```

#### Type Variables Are Not Valid in Static Contexts of Generic Classes
- ![[Pasted image 20230807133142.png]]
- 
#### You can't Throw or Catch Instances of a Generic class
- You can neither throw nor catch objects of a generic class.
- In fact, it is not even legal for a generic class to extend `Throwable`.
```Java
public class Problem extends Exception { /* . . . */ } 
// ERROR--can't extend Throwable
```
- You cannot use a type variable in a `catch` clause.
```Java
catch (T e) // ERROR--can't catch type variable 
{ 
	Logger.global.info(. . .); 
}
```
- However, it is OK to use type variables in exception specifications.
```Java
public static <T extends Throwable> void d()
{
	. . .
}
```
#### Beware of Clashes after Erasure
- It is illegal to create conditions that cause clashes when generic types are erased.
- For example, the following is illegal:
```Java
class Employee implements Comparable { . . . }
class Manager extends Employee implements Comparable { . . . } // ERROR
```
- Manager would then implement both `Comparable<Employee>` and `Comparable<Manager>`, which are different parameterizations of the same interface.


# Inheritance rules for Generic Types
- Consider a class and a subclass, such as `Employee` and `Manager`. Is `Pair<Manager>` a subclass of `Pair<Employee>` ? Perhaps surprisingly, the answer is **NO**.
- In general, there is no relationship between `Pair<S>` and `Pair<T>`, no matter how S and T are related.

![[Pasted image 20230731200716.png]]

- Finally, generic classes **can extend or implement** other generic classes. In this regard, they are no different from ordinary classes.

![[Pasted image 20230731200851.png]]

# Wildcard Types

### The Wildcard Concept
- In a wildcard type, a type parameter is allowed to vary.

For example, the wildcard type (subtype bound)
```Java
Pair<? extends Employee>
```
denotes any generic `Pair` type whose type parameter is a subclass of `Employee`, such as
`Pair<Manager>`, but not `Pair<String>`.

#### Example

Let’s say you want to write a method that prints out pairs of employees, like this:

```Java
public static void printBuddies(Pair<Employee> p)
{
	. . .
}
```
Here you can't pass a `Pair<Manager>` . so do this instead:
```Java
public static void printBuddies(Pair<? extends Employee> p)
```

![[Pasted image 20230731201449.png]]
![[Pasted image 20230807134228.png]]
### Supertype bounds for wildcards
Wildcard bounds are similar to type variable bounds, but they have an added capability—you can specify a supertype bound, like this:

```Java
? super Manager
```

This wildcard is **restricted to all supertypes of Manager**.
![[Pasted image 20230807135002.png]]
![[Pasted image 20230807135025.png]]
![[Pasted image 20230731202825.png]]
**Figure:** A wildcard with a supertype bound

Intuitively speaking, wildcards with supertype bounds let you write to a generic object, while wildcards with subtype bounds let you read from a generic object.

###  Pair`<?>` vs raw Pair
- The type `Pair<?>` is called ***unbounded wildcard*** which has methods such as `? getFirst()` and `void setFirst(?)`.
- The return value of `getFirst` can only be assigned to an ***Object***.
- The `setFirst` method can never be called, not even with an ***Object***.
-  That’s the essential difference between `Pair<?>` and `Pair`: you can call the `setFirst` method of the raw `Pair` class with any ***Object***.

### Wildcard captures
Let us write a swap method to understand what it is:
```Java
public static <T> void swapHelper(Pair<T>p)
{
	T t = p.getFirst();
	p.setFirst(p.getSecond());
	p.setSecond(t);
}
public static void swap(Pair<?> p)
{
	/*
	Won't work, because a wildcard is not a type variable
	? t = p.getFirst();
	p.setFirst(p.getSecond());
	p.setSecond(t);
	*/
	swapHelper(p);
}
```
Here the parameter **T** of the `swapHelper` method *captures* the *wildcard*.
### Example
![[Pasted image 20230807133355.png]]

# Reflection and Generics (Unfinished)
- Reflection lets you analyze arbitrary objects at runtime.
- If the objects are instances of generic classes, you don't get much info about the generic type parameters because they have been erased.
### The Generic `Class` Class
- The `Class` class is now generic.
- For example, **String.class** is actually an object (in fact, the sole object) of the class `Class<String>`
### Using `class<T>` Parameters for Type matching

It is sometimes useful to match the type variable of a `Class<T>` parameter in a generic method. For Example:
```Java
public static <T> Pair<T> makePair(Class<T> c) throws InstantiationException,IllegalAccessException
{
	return new Pair<>(c.newInstance(),c.newInstance());
}

//if you call
makePair(Employee.class)
```
then `Employee.class` is an object of type `Class<Employee>`.The type parameter **T** matches the class `Employee`. So this works and the `newInstance()` method creates instance of the Employee and the compiler can infer that the method returns a `Pair<Employee>`.