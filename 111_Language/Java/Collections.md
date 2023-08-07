# The Java Collections Framework

### Separating Collection Interfaces and Implementation
- Take an example of `Queue` interface
	- The interface tells you nothing about how the queue is implemented. Of the two common implementations of a queue, one uses a ***circular array*** and one uses a ***linked list***.
- Therefore it makes sense to use the *interfacce type* to hold the collection reference, in this way you can easily use a different implementation of that interface later if you want to.
- ![[Pasted image 20230807192920.png]]
- ![[Pasted image 20230807192936.png]]

### The Collection interface
- The fundamental interface for collection classes in the Java library is the `Collection` interface.
- ![[Pasted image 20230807193208.png]]
- The add method adds an element to the collection and returns true if the collection is changed otherwise returns false.
- The `iterator` method ***returns an object that implements*** the `Iterator` interface.
- You can use the `iterator` object to visit the elements in the collection one by one.

### Iterators
- The Iterator interface has four methods :
- ![[Pasted image 20230807193608.png]]
- ![[Pasted image 20230807193947.png]]
- The “for each” loop works with any object that implements the `Iterable` interface, an interface with a single `abstract` method:
- ![[Pasted image 20230807194034.png]]
- If you want to use the `remove` method of the `Iterator` interface, you need to skip over the element to be removed using `next()` method, only then you can call `rmeove` or else you will get `IllegalStateException`.
- ![[Pasted image 20230807194557.png]]
- ![[Pasted image 20230807194614.png]]

### Generic Utility Methods
- ![[Pasted image 20230807195016.png]]
- ![[Pasted image 20230807195051.png]]
- Of course, it is a bother if every class that implements the `Collection` interface has to supply so many routine methods. To make life easier for implementors, the library supplies a class `AbstractCollection` that leaves the fundamental methods `size` and `iterator` `abstract` but implements the routine methods in terms of them.
- ![[Pasted image 20230807195943.png]]

# Interfaces in the Collections Framework
- ![[Pasted image 20230807195128.png]]
- The `ListIterator` interface is a `subinterface` of Iterator. It defines a method for adding an element before the iterator position: `void add(E element)`.
- The `SortedSet` and `SortedMap` interfaces expose the comparator object used for sorting, and they define methods to obtain views of subsets of the collections.
- `NavigableSet` and `NavigableMap` contain additional methods for searching and traversal in sorted sets and maps.
- The `TreeSet` and `TreeMap` classes implement these interfaces.

# Concrete Collections
- ![[Pasted image 20230807195812.png]]
- ![[Pasted image 20230807200317.png]]