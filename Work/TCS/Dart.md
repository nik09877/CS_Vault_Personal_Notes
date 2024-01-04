# DART

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

# Stateful and Stateless Widgets

In Flutter, widgets are the basic building blocks of the user interface. Widgets can be categorized into two main types: stateful widgets and stateless widgets.

### 1. **Stateless Widgets:**

A stateless widget is a widget that doesn't store any mutable state. Once created, its properties cannot change. Stateless widgets are used for parts of the user interface that don't change dynamically. They are essentially static and don't have internal state that changes over time.

Example of a stateless widget:

```dart
import 'package:flutter/material.dart';

class MyStatelessWidget extends StatelessWidget {
  final String title;

  MyStatelessWidget({required this.title});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(title),
      ),
      body: Center(
        child: Text('This is a Stateless Widget'),
      ),
    );
  }
}
```

In this example, `MyStatelessWidget` is a stateless widget. It takes a `title` as a parameter, and once the widget is built, the title cannot be changed.

### 2. **Stateful Widgets:**

A stateful widget is a widget that can change its state during its lifetime. Stateful widgets are used for dynamic parts of the user interface that can be updated based on user interactions, data changes, etc. They have an associated mutable state object that can be modified.

Example of a stateful widget:

```dart
import 'package:flutter/material.dart';

class MyStatefulWidget extends StatefulWidget {
  final String title;

  MyStatefulWidget({required this.title});

  @override
  _MyStatefulWidgetState createState() => _MyStatefulWidgetState();
}

class _MyStatefulWidgetState extends State<MyStatefulWidget> {
  int counter = 0;

  void incrementCounter() {
    setState(() {
      counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(widget.title),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text('Counter: $counter'),
            ElevatedButton(
              onPressed: incrementCounter,
              child: Text('Increment'),
            ),
          ],
        ),
      ),
    );
  }
}
```

In this example, `MyStatefulWidget` is a stateful widget. It has an associated `_MyStatefulWidgetState` class that holds the mutable state (`counter` in this case). The `incrementCounter` method is used to update the state, and `setState` is called to trigger a rebuild of the widget.

### Key Points:

- Stateless widgets are immutable and don't have mutable state.
- Stateful widgets have mutable state and can be updated over time.
- Stateful widgets have a corresponding state class that extends `State`.
- `setState` is used to notify Flutter to rebuild the widget when the state changes.

Understanding the distinction between stateful and stateless widgets is fundamental when working with Flutter, as it influences how you design and structure your UI components.