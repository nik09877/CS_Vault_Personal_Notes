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
### Linked Lists
- Used for Fast insertion and deletion.
- There is no `add` method in the `Iterator` inter-face. Instead, the `Collections` library supplies a sub interface `ListIterator` that contains an `add` method.
- This `add` method adds the new element before the iterator position , it does not return a `boolean` value like the `add` method of the `Collection` interface.
- For example, the following code skips past the first element in the linked list and adds "Juliet" before the second element :
- ![[Pasted image 20230807221723.png]]
- Finally, a `set` method replaces the last element, returned by a call to `next` or `previous`, with a new element.
- ![[Pasted image 20230807221958.png]]
- If an iterator finds that its collection has been modified by another iterator or by a method of the collection itself, it throws a `ConcurrentModificationException`.
- ![[Pasted image 20230807222134.png]]
- You should never use the random access method `get()` to step through a linked list.
- ![[Pasted image 20230807222300.png]]
- The `get` method has one slight optimization: If the index is at least `size() / 2`, the search for the element ***starts at the end of the list***.
- List Interface Methods :
- ![[Pasted image 20230807222624.png]]
- `ListIterator` Methods :
- ![[Pasted image 20230807222700.png]]
- `LinkedList` Class Methods :
- ![[Pasted image 20230807222737.png]]

### Generic Array Lists
- `ArrayList` is a generic class with a type parameter.

#### Declaring Array Lists
```Java
ArrayList<Employee> staff = new ArrayList<Employee>();
//or
var staff = new ArrayList<Employee>();
//or
ArrayList<Employee> staff = new ArrayList<>();

var elements = new ArrayList<>(); // returns ArrayList<Object>
```
- If you call add and the internal array is full, the array list automatically creates a bigger array and copies all the objects from the smaller to the bigger array.
- ![[Pasted image 20230806180249.png]]
- Methods:
- ![[Pasted image 20230806180503.png]]
- ![[Pasted image 20230806180545.png]]
- ![[Pasted image 20230806180611.png]]

### Array Lists vs Vectors
- All methods of the `Vector` class are ***synchronized***.
- It is safe to access a `Vector` object from two threads. But if you access a `vector` from only a single thread, your code wastes quite a bit of time with *synchronization*.
- In contrast, the `ArrayList` methods are not synchronized. 
- It is recommended to use an `ArrayList` instead of a `Vector` whenever you don’t need synchronization.

### Hash Sets
- You should only use a `HashSet` if you don’t care about the ordering of the elements in the collection.
- It stores only unique items.
- In Java, hash tables are implemented as arrays of linked lists.
- Each list is called a *bucket*.
- To find the place of an object in the table, compute its `hash code` and reduce it modulo **the total number of buckets**. The resulting number is the index of the bucket that holds the element.
- Of course, sometimes you will hit a bucket that is already filled. This is called a **hash collision**.
- Then, compare the new object with all objects in that bucket to see if it is already present.
- ![[Pasted image 20230807231744.png]]
- As of Java 8, the buckets change **from linked lists into balanced binary trees when they get full.** This improves performance if a hash function was poorly chosen and yields many collisions, or if malicious code tries to flood a hash table with many values that have identical hash codes.
- If you want more control over the performance of the hash table, you can specify the initial bucket count.
	- You should set it to somewhere between 75% and 150% of the expected element count.
	- The standard library uses bucket counts that are powers of 2, with a default of **16**. 
	- Any value you supply for the table size is automatically rounded to the next power of 2.
- If the hash table gets too full, it needs to be ***rehashed***.
	- To rehash the table, a table with more buckets is created, all elements are inserted into the new table, and the original table is discarded.
	- The load factor determines when a hash table is rehashed.
	- For example, if the load factor is 0.75 (which is the default) and the table is more than 75% full, it is automatically rehashed with twice as many buckets. 
- ![[Pasted image 20230807232710.png]]
- Example :
- ![[Pasted image 20230807232609.png]]

### Tree Sets
- A `Tree set` similar to `Hash Set`, but it is a sorted collection.
- The sorting is accomplished by a tree data structure. (The current implementation uses a red-black tree.
- In order to use a `Tree set`, you must be able to compare the elements.
- The elements must implement the `Comparable` interface, or you must supply a `Comparator` when constructing the set.
- ![[Pasted image 20230807233507.png]]
- Example :
- ![[Pasted image 20230807233540.png]]

### Queues and Deques
 - Deque interface is implemented by the `ArrayDeque` and `LinkedList` classes.
 - ![[Pasted image 20230808001216.png]]
### Priority Queues
- By default it is a **min-heap**.
- Just like a `TreeSet`, a `priority queue`can either hold elements of a class that implements the `Comparable` interface or a `Comparator` object you supply in the constructor.
- ![[Pasted image 20230808001507.png]]
- ![[Pasted image 20230808001531.png]]

# Maps
- It stores `[key,value]` pairs.
- All keys must be unique or else it replaces the old value with new value if same key is used again.
### Basic Map Operations
- Methods :
- ![[Pasted image 20230808002053.png]]
- Example :
- ![[Pasted image 20230808002120.png]]
### Updating Map Entries
- Consider using a map for counting how often a word occurs in a file. When we see a word, we’d like to increment a counter by 1.
- ![[Pasted image 20230808002625.png]]
- ![[Pasted image 20230808002641.png]]
### Map Views
- Map is not a `Collection`, however you can obtain *views* of the map i.e objects that implement the `Collection` interface or one of its sub interfaces.
- There are three views:
	1. set of keys : `Set<K> keySet()`
	2. collection of values : `Collection<V> values()`
	3. set of [key, value] pairs of the map : `Set<Map.Entry<k,V>> entrySet()`
		- The elements of the `entrySet` are objects of a class implementing the `Map.Entry` interface.
- For example, you can enumerate all keys of a map :
- ![[Pasted image 20230808003501.png]]
- If you invoke the `remove` method of the iterator on the `keySet` view, you actually remove the key and its associated value from the map. However, you cannot add an element to the `keySet` view.
- If you want to look at both keys and values :
- ![[Pasted image 20230808003829.png]]
- ![[Pasted image 20230808004017.png]]

### Weak Hash Maps
- The `WeakHashMap` class was designed to solve an interesting problem.
- What happens with a value whose key is no longer used anywhere in your program?
	- Suppose the last reference to a key has gone away. Then, there is no longer any way to refer to the value object. But, as no part of the program has the key any more, the key/value pair cannot be removed from the map.
- Why can’t the garbage collector remove it? Isn’t it the job of the garbage collector to remove unused objects?
	- The garbage collector traces live objects. As long as the map object is live, all buckets in it are live and won’t be reclaimed.
- You can use a `WeakHashMap` for this.
- This data structure cooperates with the garbage collector to remove key/value pairs when the only reference to the key is the one present in the hash table entry.
#### Inner Working Mechanism
- The `WeakHashMap` uses` weak references` to hold keys.
- A `WeakReference` object holds a reference to another object—in our case, a hash table key.
- Normally, if the garbage collector finds that a particular object has no references to it, it simply reclaims the object. 
- However, if the object is reachable only by a `WeakReference`, the garbage collector still reclaims the object, but places the `weak reference` that led to it into a `queue`. 
- The operations of the `WeakHashMap` periodically check that `queue` for newly arrived `weak references`. 
- The arrival of a `weak reference` in the `queue` signifies that the key was no longer used by anyone and has been collected. 
- The `WeakHashMap` then removes the associated entry.

### Linked Hash Sets and Maps
- The `LinkedHashSet` and `LinkedHashMap` classes remember in which order you inserted items.
- As entries are inserted into the table, they are joined in a doubly linked list.
- ![[Pasted image 20230808005237.png]]
#### Implement LRU Cache
- A linked hash map can alternatively use **access order**, not insertion order, to iterate through the map entries.
- Every time you call get or put, the affected entry is removed from its current position and placed at the end of the linked list of entries.
- Only the position in the linked list of entries is affected, not the hash table bucket.
- To construct such a hash map, call :
- ![[Pasted image 20230808005659.png]]

### Enumeration Sets and Maps
- The `EnumSet` is an efficient set implementation with elements that belong to an enumerated type.
- The `EnumSet` is internally implemented simply as a sequence of bits. A bit is turned on if the corresponding value is present in the set.
- The `EnumSet` class has no public constructors. Use a static factory method to construct the set :
- ![[Pasted image 20230808010122.png]]
- An `EnumMap` is a map with keys that belong to an enumerated type.
- It is simply and efficiently implemented as an array of values.
- You need to specify the key type in the constructor :
- ![[Pasted image 20230808010206.png]]
### Identity Hash Maps
- The `IdentityHashMap` has a quite specialized purpose. 
- Here, the hash values for the keys should not be computed by the `hashCode` method but by the `System.identityHashCode` method. 
- That’s the method that `Object.hashCode` uses to compute a hash code from the object’s memory address. 
- Also, for comparison of objects, the `IdentityHashMap` uses `==` not `equals`. 
	- In other words, different key objects are considered distinct even if they have equal contents. 
- This class is useful for implementing object traversal algorithms, such as object serialization, in which you want to keep track of which objects have already been traversed.
API :
![[Pasted image 20230808010440.png]]

# Views and Wrappers
