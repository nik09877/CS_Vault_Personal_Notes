# DART
 [Dart Tutorial](https://dart-tutorial.com)

Dart is a versatile programming language used for building web, mobile, and desktop applications. 

### 1. **Hello, World!**

In Dart, you can use the `print` function to output text to the console. Here's a simple "Hello, World!" program:

```dart
void main() {
  print('Hello, World!');
}
```

- `void main()`: This is the entry point of a Dart program. Dart programs start execution from the `main` function.
- `print('Hello, World!')`: This line prints the specified text to the console.

### 2. **Variables and Data Types**

Dart is a statically-typed language, meaning you need to declare the type of a variable. Here are some common data types:

```dart
void main() {
  // Variables
  int age = 25; // Integer
  double height = 5.9; // Double (floating-point number)
  String name = 'John'; // String
  bool isStudent = true; // Boolean

  // Printing variables
  print('Name: $name, Age: $age, Height: $height, Is Student: $isStudent');
}
```

- `int`: Represents integers.
- `double`: Represents floating-point numbers.
- `String`: Represents sequences of characters.
- `bool`: Represents boolean values (`true` or `false`).

### 3. **Functions**

Functions in Dart are defined using the `void` keyword (if they don't return a value) or specifying the return type. Here's an example:

```dart
void greet(String name) {
  print('Hello, $name!');
}

String getGreeting(String name) {
  return 'Hello, $name!';
}

void main() {
  greet('Alice');
  String greeting = getGreeting('Bob');
  print(greeting);
}
```

- `void greet(String name)`: A function that takes a parameter `name` of type `String` and prints a greeting.
- `String getGreeting(String name)`: A function that takes a parameter `name` and returns a greeting as a `String`.
- Function calls: `greet('Alice')` and `getGreeting('Bob')` demonstrate how to call functions.

### 4. **Control Flow: if-else Statements**

Dart supports standard control flow statements like `if`, `else`, and `else if`:

```dart
void main() {
  int age = 17;

  if (age >= 18) {
    print('You are an adult.');
  } else if (age >= 13) {
    print('You are a teenager.');
  } else {
    print('You are a child.');
  }
}
```

### 5. **Lists and Loops**

Dart provides lists (arrays) and various types of loops. Here's an example:

```dart
void main() {
  // List
  List<String> fruits = ['Apple', 'Banana', 'Orange'];

  // Loop through the list
  for (String fruit in fruits) {
    print(fruit);
  }

  // While loop
  int i = 0;
  while (i < fruits.length) {
    print(fruits[i]);
    i++;
  }
}
```

- `List<String> fruits`: Declares a list of strings.
- `for (String fruit in fruits)`: Iterates over each element in the list.
- `while (i < fruits.length)`: Demonstrates a `while` loop.

### 6. **Classes and Objects**

Dart is an object-oriented language. Here's a basic example of a class:

```dart
class Person {
  String name;
  int age;

  // Constructor
  Person(this.name, this.age);

  void introduceYourself() {
    print('Hello, my name is $name, and I am $age years old.');
  }
}

void main() {
  // Creating an object of the Person class
  Person person = Person('Alice', 30);

  // Accessing object properties
  print('Name: ${person.name}, Age: ${person.age}');

  // Calling a method on the object
  person.introduceYourself();
}
```

- `class Person`: Defines a class named `Person` with properties and methods.
- `Person(this.name, this.age)`: Constructor shorthand for initializing properties.
- `void introduceYourself()`: A method within the `Person` class.

These are some foundational concepts in Dart. More advanced topics like asynchronous programming, exception handling, and more. Dart's official documentation is an excellent resource for in-depth learning: [Dart Documentation](https://dart.dev/guides).
