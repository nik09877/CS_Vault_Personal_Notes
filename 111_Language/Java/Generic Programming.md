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
Pair<Employee> employeePair = . . .;
if (stringPair.getClass() == employeePair.getClass()) // returns true because both return Pair.class
```
#### 3. You can't create arrays of parameterized types

```Java
Pair<String>[] table = new Pair<String>[10]; //ERROR
```
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

public static void addAll(Collection coll, T... ts)
{
	for (T t : ts) coll.add(t);
}
Collection> table = . . .;
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
#### You can;t Throw or Catch Instances of a Generic class
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
