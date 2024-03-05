
# Table of Contents
```table-of-contents
title: 
style: nestedList # TOC style (nestedList|inlineFirstLevel)
minLevel: 1 # Include headings from the specified level
maxLevel: 2 # Include headings up to the specified level
includeLinks: true # Make headings clickable
debugInConsole: false # Print debug info in Obsidian console
```
# Dart Tutorial

## Introduction to Dart
### Dart

- Dart is a client-optimized, object-oriented, modern programming language to build apps fast for many platforms like android, iOS, web, desktop, etc. 
- Client optimized means optimized for crafting a beautiful user interface and high-quality experiences. 
- Google developed Dart as a programming language.
- A solid understanding of Dart is necessary to develop high-quality apps with flutter. 

### Dart Features

*   Free and open-source.
*   Object-oriented programming language.
*   Used to develop android, iOS, web, and desktop apps fast.
*   Can compile to either native code or javascript.
*   Offers modern programming features like null safety and asynchronous programming.
*   You can even use Dart for servers and backend.

### Difference Between Dart & Flutter

*   **Dart** is a client optimized, object-oriented programming language. It is popular nowadays because of flutter. It is difficult to build complete apps only using Dart because you have to manage many things yourself.
    
*   **Flutter** is a framework that uses dart programming language. With the help of flutter, you can build apps for android, iOS, web, desktop, etc. The framework contains ready-made tools to make apps faster.
    

### Which Is The Best Code Editor For Dart Programming

The best code editor is VS Code if you want to run the dart program from a computer or laptop. You can download the dart extension from VS Code and start coding. You will learn more about [installing dart](https://dart-tutorial.com/introduction-and-basics/dart-install/) in the next topic. You can also use [DartPad](https://dartpad.dev/) to run simple dart programs without installing anything.

### Dart History

*   Google developed Dart in 2011 as an alternative to javascript.
*   Dart 1.0 was released on November 14, 2013.
*   Dart 2.0 was released in August 2018.
*   Dart 3.0 was released in May 2023.
*   Dart gained popularity in recent days because of flutter.

### Basic Programming Terms

Important words that you often hear while learning programming languages.

**Statements:** A statement is a command that tells a computer to do something. In Dart, you can end most statements with a semicolon **;**.

**Expressions:** An Expression is a value or something that can be calculated as a value. The expression can be numbers, text, or some other type. For E.g.

```dart
a. 52
b. 5+5
c. 'Hello World.'
d. num

```


**Keywords:** Keywords are reserved words that give special meaning to the dart compiler. For E.g. **int**, **if**, **var**, **String**, **const**, etc.

**Identifiers:** Identifiers are names created by the programmer to define variables, functions, classes, etc. Identifiers shouldn’t be keywords and must have a unique name. For E.g. **int age =19;**, here age is an identifier. You will learn more about identifiers later in this course.

**High-Level Programming Language:** High-Level Programming Language is easy to learn, user-friendly, and uses English-like-sentence. For E.g. dart,c,java,etc.

**Low-Level Programming Language:** Low-level programming language is hard to learn, non-user friendly, and deals with computer hardware components, e.g., machine and assembly language.

Info

Note: Low-level languages are faster than high-level but hard to understand and debug.

**Compiler:** A compiler is a computer program that translates the high-level programming language into machine-level language.

**Syntax:** The Syntax is a programming language’s pattern or rules that give the concept to code.

### Key Points

*   Dart is a free and open-source programming language. You don’t need to pay any money to run dart programs.
*   Dart is a platform-independent language and supports almost every operating system such as windows, mac, and Linux.
*   Dart is an object-oriented programming language and supports all oops features such as encapsulation, inheritance, polymorphism, interface, etc.
*   Dart comes with a **dart2js** compiler which translates dart code to javascript code that runs on all modern browsers.
*   Dart is a programming language used by flutter, the world’s most popular framework for building apps.


## Install Dart 
### **Dart Installation**

There are multiple ways to install a dart on your system. You can install Dart on **Windows, Mac, and Linux** or run it from the browser.

### **Requirements**

*   **Dart SDK**,
*   **VS code or other editors** like Intellij \[We will use VS Code here\].

### **Dart Windows Installation**

Follow the below instructions to install a dart on the windows operating system.

**Steps:**

*   Download Dart SDK from [here](https://dart.dev/get-dart/archive).
*   Copy **dart-sdk** folder to your C drive.
*   Add **C:\\dart-sdk\\bin** to your environment variable. 
*   Open the command prompt and type **`dart --version`** to check it.
*   Install [VS Code](https://code.visualstudio.com/download) and Add Dart Extension.

**Note**: Dart SDK provides the tools to compile and run dart program.

### **Dart Mac Installation**

*   Install Homebrew From [here](https://brew.sh/).
*   Type `brew tap dart-lang/dart` in the terminal.
*   Type `brew install dart` in the terminal.

### **Homebrew Install Command**

Copy and paste this command on your terminal to install Homebrew.

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

```


To set the homebrew path, copy and paste this command on your terminal.

```
export PATH=/opt/homebrew/bin:$PATH

```


### **Dart Linux Installation**

To install a dart on Linux, open your terminal and **copy/paste** the below commands.

```
sudo apt-get update
sudo apt-get install apt-transport-https
wget -qO- https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo gpg --dearmor -o /usr/share/keyrings/dart.gpg
echo 'deb [signed-by=/usr/share/keyrings/dart.gpg arch=amd64] https://storage.googleapis.com/download.dartlang.org/linux/debian stable main' | sudo tee /etc/apt/sources.list.d/dart_stable.list

```


Then, install the dart using the below command.

```
sudo apt-get update
sudo apt-get install dart

```


To set the dart path, copy and paste this command on your terminal.

```
export PATH="$PATH:/usr/lib/dart/bin"

```


### **Check Dart Installation**

Open your command prompt and type **`dart --version`**. The dart is successfully installed on your system if it gives you a version code. If not, watch the video above.

### **Some Useful Commands**


|Command                       |Description                                                    |
|------------------------------|---------------------------------------------------------------|
|dart --help                   |Show all available commands.                                   |
|dart filename.dart            |Run the dart file.                                             |
|dart create                   |Create a dart project.                                         |
|dart fix                      |Update dart project to new syntax.                             |
|dart compile exe bin/dart.dart|Compile dart code.                                             |
|dart compile js bin/dart.dart |Compile dart to javascript. You can run this file with Node.js.|


### **Run Dart On Web**

You can run the dart program on your browser without installing any software. Dartpad is a web tool to write and run your dart code.

*   [Run Dart Programming on Web](https://dartpad.dev/)

### **Install Dart Official Link**

*   [Install Dart Official Link](https://dart.dev/get-dart)

### **Can You Run Dart From Mobile?**

Yes, you can use [DartPad](https://dartpad.dev/) to run simple dart programs from your phone without installing any software. For bigger projects, using DartPad is not recommended.

## Basic Dart Program 

This is a simple dart program that prints **Hello World** on screen. Most programmers write the Hello World program as their first program.

```
void main() { 
   print("Hello World!"); 
}

```


[Run Online](https://dartpad.dev/?id=2a27a92364b348df4953f880518af7a3)

### **Basic Dart Program Explained**

*   void main() is the starting point where the execution of your program begins.
*   Every program starts with a main function.
*   The curly braces {} represent the beginning and the ending of a block of code.
*   print(“Hello World!”); prints Hello World! on screen.
*   Each code statement must end with a semicolon.

### **Basic Dart Program For Printing Name**

```
void main()
{
    var name = "John";
    print(name);
}

```


[Run Online](https://dartpad.dev/?id=52502e861f491ed1b28a6da73b53efba)

### **Dart Program To Join One Or More Variables**

Here **$variableName** is used to join variables. This joining process in dart is called string interpolation.

```
void main(){
  var firstName = "John";
  var lastName = "Doe";
  print("Full name is $firstName $lastName");
}

```


[Run Online](https://dartpad.dev/?id=caa95bbad26818e23a292938ceba4d3a)

### **Dart Program For Basic Calculation**

Performing addition, subtraction, multiplication, and division in dart.

```
void main() {
int num1 = 10; //declaring number1
int num2 = 3; //declaring number2
  
// Calculation
int sum = num1 + num2;
int diff = num1 - num2;
int mul = num1 * num2;
double div = num1 / num2; // It is double because it outputs number with decimal.
  
// displaying the output
print("The sum is $sum");
print("The diff is $diff");
print("The mul is $mul");
print("The div is $div");
}

```


[Run Online](https://dartpad.dev/?id=5de9dc2148637e9d9ecbd98632b457e6)

### **Create Full Dart Project**

It’s nice to work on a single file, but if your project gets bigger, you need to manage configurations, packages, and assets files. So creating a dart project will help you to manage this all.

```
dart create <project_name>

```


This will create a simple dart project with some ready-made code.

### **Steps To Create Dart Project**

*   Open folder location on command prompt/terminal.
*   Type `dart create project_name` (For E.g. dart create first\_app)
*   Type `cd first_app`
*   Type `code .` to open project with visual studio code
*   To check the main dart file go to **bin/first\_app.dart** and edit your code.

### **Run Dart Project**

First, open the project location on the command/terminal and run the project with this command.
```dart
dart run
```

### **Convert Dart Code To Javascript**


|Command                      |Description                                                    |
|-----------------------------|---------------------------------------------------------------|
|dart compile js filename.dart|Compile dart to javascript. You can run this file with Node.js.|


## Variables in Dart
### **Variables**

Variables are containers used to store value in the program. There are different types of variables where you can keep different kinds of values. Here is an example of creating a variable and initializing it.

```
// here variable name contains value John.
var name = "John";

```


### **Variable Types**

They are called data types. We will learn more about data types later in this dart tutorial.

*   **String**: For storing text value. E.g. “John” \[Must be in quotes\]
*   **int**: For storing integer value. E.g. 10, -10, 8555 \[Decimal is not included\]
*   **double**: For storing floating point values. E.g. 10.0, -10.2, 85.698 \[Decimal is included\]
*   **num**: For storing any type of number. E.g. 10, 20.2, -20 \[both int and double\]
*   **bool**: For storing true or false. E.g. true, false \[Only stores true or false values\]
*   **var**: For storing any value. E.g. ‘Bimal’, 12, ‘z’, true

### **Syntax**

This is syntax for creating a variable in dart.

```
type variableName = value;

```


### **Example 1: Using Variables In Dart**

In this example, you will learn how to declare variables and print their values.

```
void main() {
// declaring variables
String name = "John";
String address = "USA";  
num age = 20; // used to store any types of numbers 
num height = 5.9;
bool isMarried = false;
   
// printing variables value   
print("Name is $name");
print("Address is $address");
print("Age is $age");
print("Height is $height");
print("Married Status is $isMarried");
}

```


[Run Online](https://dartpad.dev/?id=e050476fb9a1afa27732106f52d38d68)

**Note**: Always use the descriptive variable name. Don’t use a variable name like a, b, c because this will make your code more complex.

### **Rules For Creating Variables In Dart**

*   Variable names are case sensitive, i.e., a and A are different.
*   A variable name can consist of letters and alphabets.
*   A variable name cannot start with a number.
*   Keywords are not allowed to be used as a variable name.
*   Blank spaces are not allowed in a variable name.
*   Special characters are not allowed except for the underscore (\_) and the dollar ($) sign.

### **Dart Constant**

Constant is the type of variable whose value never changes. In programming, changeable values are **mutable** and unchangeable values are **immutable**. Sometimes, you don’t need to change the value once declared. Like the value of PI=3.14, it never changes. To create a constant in Dart, you can use the const keyword.

```
void main(){
const pi = 3.14;
pi = 4.23; // not possible  
print("Value of PI is $pi");
}

```


[Run Online](https://dartpad.dev/?id=7fd7914f845a1c8ec59b89e00ead5916)

### **Naming Convention For Variables In Dart**

It is a good habit to follow the naming convention. In Dart Variables, the variable name should start with lower-case, and every second word’s first letter will be upper-case like num1, fullName, isMarried, etc. Technically, this naming convention is called **lowerCamelCase**.

### **Naming Convention Example**

```
// Not standard way
var fullname = "John Doe";
// Standard way
var fullName = "John Doe";
const pi = 3.14;

```


## Data Types in Dart
### **Data Types**

**Data types** help you to categorize all the different types of data you use in your code. **For e.g. numbers, texts, symbols, etc**. The data type specifies what type of value will be stored by the variable. Each variable has its data type. Dart supports the following built-in data types :

1.  Numbers
2.  Strings
3.  Booleans
4.  Lists
5.  Maps
6.  Sets
7.  Runes
8.  Null

### **Built-In Types**

In Dart language, there is the type of values that can be represented and manipulated. The data type classification is as given below:


|Data Type|Keyword         |Description                                           |
|---------|----------------|------------------------------------------------------|
|Numbers  |int, double, num|It represents numeric values                          |
|Strings  |String          |It represents a sequence of characters                |
|Booleans |bool            |It represents Boolean values true and false           |
|Lists    |List            |It is an ordered group of items                       |
|Maps     |Map             |It represents a set of values as key-value pairs      |
|Sets     |Set             |It is an unordered list of unique values of same types|
|Runes    |runes           |It represents Unicode values of String                |
|Null     |null            |It represents null value                              |


### **Numbers**

When you need to store numeric value on dart, you can use either int or double. Both int and double are subtypes of **num**. You can use num to store both int or double value.

```
void main() {
// Declaring Variables  
int num1 = 100; // without decimal point.
double num2 = 130.2; // with decimal point.
num num3 = 50;
num  num4 = 50.4;  

// For Sum   
num sum = num1 + num2 + num3 + num4;
   
// Printing Info   
print("Num 1 is $num1");
print("Num 2 is $num2");  
print("Num 3 is $num3");  
print("Num 4 is $num4");  
print("Sum is $sum");  
   
}

```


[Run Online](https://dartpad.dev/?id=7be7e0aa5918419c03b55d27222d4820)

### **Round Double Value To 2 Decimal Places**

The `.toStringAsFixed(2)` is used to round the double value upto 2 decimal places in dart. You can round to any decimal places by entering numbers like 2, 3, 4, etc.

```
void main() {
// Declaring Variables
double price = 1130.2232323233233; // valid.
print(price.toStringAsFixed(2));
}

```


[Run Online](https://dartpad.dev/?id=cf1299853b81c55dad6539147bab4bd4)

### **String**

String helps you to store text data. You can store values like **I love dart**, **New York 2140** in String. You can use single or double quotes to store string in dart.

```
void main() {
// Declaring Values     
String schoolName = "Diamond School";
String address = "New York 2140";   

// Printing Values
print("School name is $schoolName and address is $address");   
}

```


[Run Online](https://dartpad.dev/?id=babf76424f9daaafcb0c522b39fafdfe)

### **Create A Multi-Line String In Dart**

If you want to create a multi-line String in dart, then you can use triple quotes with either single or double quotation marks.

```
void main() {
// Multi Line Using Single Quotes   
String multiLineText = '''
This is Multi Line Text
with 3 single quote
I am also writing here.
''';
   
// Multi Line Using Double Quotes   
String otherMultiLineText = """
This is Multi Line Text
with 3 double quote
I am also writing here.
""";
   
// Printing Information   
print("Multiline text is $multiLineText");
print("Other multiline text is $otherMultiLineText");
}

```

[Run Online](https://dartpad.dev/?id=d97095b4bf9822a4838cc6c3571cc457)

### **Special Character In String**


|Special Character|Work    |
|-----------------|--------|
|\n               |New Line|
|\t               |Tab     |


```
void main() {
   
// Using \n and \t   
print("I am from \nUS.");
print("I am from \tUS.");
}

```


[Run Online](https://dartpad.dev/?id=0fd1cb69933acb4686e9523ef8e839c6)

### **Create A Raw String In Dart**

You can also create raw string in dart. Special characters won’t work here. You must write **r** after equal sign.

```
void main() {
// Set price value
num price = 10;
String withoutRawString = "The value of price is \t $price"; // regular String
String withRawString =r"The value of price is \t $price"; // raw String

print("Without Raw: $withoutRawString"); // regular result
print("With Raw: $withRawString"); // with raw result

}

```

[Run Online](https://dartpad.dev/?id=d2d0263d6e80d92a1e5f845e1074963b)

### **Type Conversion In Dart**

In dart, type conversion allows you to convert one data type to another type. For e.g. to convert String to int, int to String or String to bool, etc.

### **Convert String To Int In Dart**

You can convert String to int using int.parse() method. The method takes String as an argument and converts it into an integer.

```
void main() {
String strvalue = "1";
print("Type of strvalue is ${strvalue.runtimeType}");   
int intvalue = int.parse(strvalue);
print("Value of intvalue is $intvalue");
// this will print data type
print("Type of intvalue is ${intvalue.runtimeType}");
}

```


[Run Online](https://dartpad.dev/?id=93c9156125508d1344a8324dd337aa6a)

### **Convert String To Double In Dart**

You can convert String to double using double.parse() method. The method takes String as an argument and converts it into a double.

```
void main() {
String strvalue = "1.1";
print("Type of strvalue is ${strvalue.runtimeType}");
double doublevalue = double.parse(strvalue);
print("Value of doublevalue is $doublevalue");
// this will print data type
print("Type of doublevalue is ${doublevalue.runtimeType}");
}

```


[Run Online](https://dartpad.dev/?id=35e0e9928eac53ff2f15b75ec690942a)

### **Convert Int To String In Dart**

You can convert int to String using the toString() method. Here is example:

```
void main() {
int one = 1;
print("Type of one is ${one.runtimeType}");
String oneInString = one.toString(); 
print("Value of oneInString is $oneInString");
// this will print data type
print("Type of oneInString is ${oneInString.runtimeType}");
}

```

[Run Online](https://dartpad.dev/?id=b70894081c9642a9c5626cfc5ecb14c9)

### **Convert Double To Int In Dart**

You can convert double to int using the toInt() method.

```
void main() { 
   double num1 = 10.01;
   int num2 = num1.toInt(); // converting double to int

  print("The value of num1 is $num1. Its type is ${num1.runtimeType}");
  print("The value of num2 is $num2. Its type is ${num2.runtimeType}");
}

```
[Run Online](https://dartpad.dev/?id=91723c90e7aa0c5e55b3f15866e9dbc0)

### **Booleans**

In Dart, boolean holds either true or false value. You can write the **bool** keyword to define the boolean data type. You can use boolean if the answer is true or false. Consider the answer to the following questions:

*   Are you married?
*   Is the door open?
*   Does a cat fly?
*   Is the traffic light green?
*   Are you older than your father?

**These all are yes/no questions. Its a good idea to store them in boolean.**

```
void main() {
bool isMarried = true;
print("Married Status: $isMarried");
}

```

[Run Online](https://dartpad.dev/?id=affed489d713e7b1a193dbc01c080425)

### **Lists**

The list holds multiple values in a single variable. It is also called arrays. If you want to store multiple values without creating multiple variables, you can use a list.

```
void main() {
List<String> names = ["Raj", "John", "Max"];
print("Value of names is $names");
print("Value of names[0] is ${names[0]}"); // index 0
print("Value of names[1] is ${names[1]}"); // index 1
print("Value of names[2] is ${names[2]}"); // index 2

  // Finding Length of List 
int length = names.length;  
print("The Length of names is $length");
}

```


[Run Online](https://dartpad.dev/?id=ef8ac2962eafb87626cff2d0a72631ef)

Info

**Note**: List index always starts with 0. Here names\[0\] is Raj, names\[1\] is John and names\[2\] is Max.

### **Sets**

An unordered collection of unique items is called set in dart. You can store unique data in sets.

Info

Note: Set doesn’t print duplicate items.

```
void main() {
Set<String> weekday = {"Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"};
print(weekday);
}

```


[Run Online](https://dartpad.dev/?id=19097581fa56c7d5322da870e121a33c)

### **Maps**

In Dart, a map is an object where you can store data in key-value pairs. Each key occurs only once, but you can use same value multiple times.

```
void main() {
Map<String, String> myDetails = {
   'name': 'John Doe',
   'address': 'USA',
   'fathername': 'Soe Doe'
};
// displaying the output
print(myDetails['name']);
}

```


[Run Online](https://dartpad.dev/?id=38f9825722404dd6f31d259ea52605d6)

### **Var Keyword In Dart**

In Dart, **var** automatically finds a data type. In simple terms, var says if you don’t want to specify a data type, I will find a data type for you.

```
void main(){

var name = "John Doe"; // String
var age = 20; // int

print(name);
print(age);
}

```

[Run Online](https://dartpad.dev/?id=ba9debaeebf20409ddf8e59b3f4daa22)

### **Runes In Dart**

With runes, you can find Unicode values of String. The Unicode value of **a** is **97**, so runes give 97 as output.

```
void main() {

String value = "a";
print(value.runes);
}

```

[Run Online](https://dartpad.dev/?id=eb53d4079e1051f22bc2950de78ac241)

### **How To Check Runtime Type**

You can check runtime type in dart with `.runtimeType` after the variable name.

```
void main() { 
   var a = 10;
   print(a.runtimeType); 
   print(a is int); // true
}

```

[Run Online](https://dartpad.dev/?id=b15e41105a5b65c6ca0daaf8d00bf595)

### **Optionally Typed Language**

You may have heard of the **statically-typed** language. It means the data type of variables is known at compile time. Similarly, **dynamically-typed** language means data types of variables are known at run time. Dart supports dynamic and static types, so it is called optionally-typed language.

### **Statically Typed**

A language is statically typed if the data type of variables is known at compile time. Its main advantage is that the compiler can quickly check the issues and detect bugs.

```
void main() { 
   var myVariable = 50; // You can also use int instead of var
   myVariable = "Hello"; // this will give error
   print(myVariable);
}

```

[Run Online](https://dartpad.dev/?id=9d93d16d1fd115524698bdd9510f84c7)

### **Dynamically Typed Example**

A language is dynamically typed if the data type of variables is known at run time.

```
void main() { 
   dynamic myVariable = 50;
   myVariable = "Hello";
   print(myVariable);
}

```

[Run Online](https://dartpad.dev/?id=7db07c7c42b1408649cae9276817a1bf)

**Note**: Using static type helps you to prevent writing silly mistakes in code. It’s a good habit to use static type in dart.

## Comments in Dart 
**Comments** are the set of statements that are ignored by the dart compiler during program execution. They are used to explain the code so that you or other people can understand it easily.

*   You can describe your code.
*   Other people will understand your code more clearly.

*   **Single-Line Comment**: For commenting on a single line of code. E.g. // This is a single-line comment.
*   **Multi-Line Comment**: For commenting on multiple lines of code. E.g. /\* This is a multi-line comment. \*/
*   **Documentation Comment**: For generating documentation or reference for a project/software package. E.g. /// This is a documentation comment

Single line comments start with `//` in dart. You can write `//` and your text.

```
void main() {
// This is single-line comment.
print("Welcome to Technology Channel.");
}

```


[Run Online](https://dartpad.dev/?id=f7b3ff31a94bb2bb0ddbbc4c57d08ab7)

Multi-line comments start with `/*` and end with `*/` . You can write your comment inside `/*` and `*/`.

```
void main(){  
/*
This is a multi-line comment.
*/
    print("Welcome to Technology Channel.");  
}  

```


[Run Online](https://dartpad.dev/?id=2eb2cb81bf3019e0838e5019656f0e25)

Documentation comments are helpful when you are writing documentation for your code. Documentation comments start with `///` in dart.

```
void main(){  
/// This is documentation comment
    print("Welcome to Technology Channel.");  
}  

```


[Run Online](https://dartpad.dev/?id=ce68f8c0b69d6ef7a0b7b7f8c0f1bd14)

## Operators in Dart 

Operators are used to perform mathematical and logical operations on the variables. Each operation in dart uses a symbol called the operator to denote the type of operation it performs. Before learning operators in the dart, you must understand the following things.

*   **Operands** : It represents the data.
*   **Operator** : It represents how the operands will be processed to produce a value.

Info

**Note**: Suppose the given expression is 2 + 3. Here 2 and 3 are operands, and `+` is the operator.

### **Types Of Operators**

There are different types of operators in dart. They are as follows:

*   **Arithmetic Operators**
*   **Increment and Decrement Operators**
*   **Assignment Operators**
*   **Logical Operators**
*   **Type Test Operators**

### **Arithmetic Operators**

Arithmetic operators are the most common types of operators. They perform operations like addition, subtraction, multiplication, division, etc.


|Operator Symbol|Operator Name   |Description                                         |
|---------------|----------------|----------------------------------------------------|
|+              |Addition        |For adding two operands                             |
|-              |Subtraction     |For subtracting two operands                        |
|-expr          |Unary Minus     |For reversing the sign of the expression            |
|*              |Multiplication  |For multiplying two operands                        |
|/              |Division        |For dividing two operands and give output in double |
|~/             |Integer Division|For dividing two operands and give output in integer|
|%              |Modulus         |Remainder After Integer Division                    |


Let’s look at how to perform arithmetic calculations in dart.

```
void main() {
 // declaring two numbers 
 int num1=10;
 int num2=3;
 
 // performing arithmetic calculation
 int sum=num1+num2;       // addition
 int diff=num1-num2;      // subtraction
 int unaryMinus = -num1;    // unary minus  
 int mul=num1*num2;       // multiplication
 double div=num1/num2;    // division
 int div2 =num1~/num2;     // integer division
 int mod=num1%num2;       // show remainder
 
//Printing info 
 print("The addition is $sum.");
 print("The subtraction is $diff.");
 print("The unary minus is $unaryMinus.");
 print("The multiplication is $mul.");
 print("The division is $div.");
 print("The integer division is $div2.");
 print("The modulus is $mod."); 
}

```


[Run Online](https://dartpad.dev/?id=cb631ee189ccf2f8d5e215f6b1834746)

### **Increment and Decrement Operators**

With increment and decrement operators, you can increase and decrease values. If ++ is used at the beginning, then it is a prefix. If it is used at last, then it is postfix.


|Operator Symbol|Operator Name |Description                                                 |
|---------------|--------------|------------------------------------------------------------|
|++var          |Pre Increment |Increase Value By 1. var = var + 1 Expression value is var+1|
|--var          |Pre Decrement |Decrease Value By 1. var = var - 1 Expression value is var-1|
|var++          |Post Increment|Increase Value By 1. var = var + 1 Expression value is var  |
|var--          |Post Decrement|Decrease Value By 1. var = var - 1 Expression value is var  |


Info

**Note**: ++var increases the value of operands, whereas var++ returns the actual value of operands before the increment.

```
void main() {
// declaring two numbers 
 int num1=0;
 int num2=0;
 
// performing increment / decrement operator  

// pre increment   
num2 = ++num1;
print("The value of num2 is $num2");

// reset value to 0 
num1 = 0;
num2 = 0;

// post increment  
num2 =  num1++;
print("The value of num2 is $num2");  
  
}

```


[Run Online](https://dartpad.dev/?id=a22b435de274f81b7553046482ecd084)

### **Assignment Operators**

It is used to assign some values to variables. Here, we are assigning 24 to the age variable.


|Operator Type|Description                  |
|-------------|-----------------------------|
|=            |Assign a value to a variable |
|+=           |Adds a value to a variable   |
|-=           |Reduces a value to a variable|
|*=           |Multiply value to a variable |
|/=           |Divided value by a variable  |


```
void main() {
  double age = 24;
  age+= 1;  // Here age+=1 means age = age + 1.
  print("After Addition Age is $age");
  age-= 1;  //Here age-=1 means age = age - 1.
  print("After Subtraction Age is $age");
  age*= 2;  //Here age*=2 means age = age * 2.
  print("After Multiplication Age is $age");
  age/= 2;  //Here age/=2 means age = age / 2.
  print("After Division Age is $age");
}

```


[Run Online](https://dartpad.dev/?id=80bd0e4ffe646c1456ce93f22f013ff5)

### **Relational Operators**

Relational operators are also called comparison operators. They are used to make a comparison.



* Operator Symbol: >
  * Operator Name: Greater than
  * Description: Used to check which operand is bigger and gives result as boolean
* Operator Symbol: <
  * Operator Name: Less than
  * Description: Used to check which operand is smaller and gives result as boolean
* Operator Symbol: >=
  * Operator Name: Greater than or equal to
  * Description: Used to check which operand is bigger or equal and gives result as boolean
* Operator Symbol: <=
  * Operator Name: Less than or equal to
  * Description: Used to check which operand is smaller or equal and gives result as boolean
* Operator Symbol: ==
  * Operator Name: Equal to
  * Description: Used to check operands are equal to each other and gives result as boolean
* Operator Symbol: !=
  * Operator Name: Not equal to
  * Description: Used to check operand are not equal to each other and gives result as boolean


```
void main() {
  
 int num1=10;
 int num2=5;
 //printing info
 print(num1==num2); 
 print(num1<num2);
 print(num1>num2);
 print(num1<=num2);
 print(num1>=num2);
}

```


[Run Online](https://dartpad.dev/?id=751428eeb99566d37edd02325f446ca8)

### **Logical Operators**

It is used to compare values.


|Operator Type|Description                                                     |
|-------------|----------------------------------------------------------------|
|&&           |This is ‘and’, return true if all conditions are true           |
|||           |This is ‘or’. Return true if one of the conditions is true      |
|!            |This is ’not’. return false if the result is true and vice versa|


```
void main(){
  int userid = 123;
    int userpin = 456;

    // Printing Info
    print((userid == 123) && (userpin== 456)); // print true
    print((userid == 1213) && (userpin== 456)); // print false.
    print((userid == 123) || (userpin== 456)); // print true.
    print((userid == 1213) || (userpin== 456)); // print true
    print((userid == 123) != (userpin== 456));//print false

}

```


[Run Online](https://dartpad.dev/?id=567ef2df99b30af3352e71dd74d92b90)

### **Type Test Operators**

In Dart, type test operators are useful for checking types at runtime.


|Operator Symbol|Operator Name|Description                                                |
|---------------|-------------|-----------------------------------------------------------|
|is             |is           |Gives boolean value true if the object has a specific type |
|is!            |is not       |Gives boolean value false if the object has a specific type|


```
void main() {
  String value1 = "Dart Tutorial";
  int age = 10;
  
  print(value1 is String);
  print(age is !int);
}

```


[Run Online](https://dartpad.dev/?id=13717bb8ae63da6004b4bb4a44bf0fb8)

## User Input in Dart 
 You must import the package `import 'dart:io';` for user input.

**Note**: You won’t be able to take input from users using dartpad. You need to run a program from your computer.

### String User Input

They are used for storing textual user input. If you want to keep values like somebody’s name, address, description, etc., you can take string input from the user.

```
import 'dart:io';

void main() {
  print("Enter name:");
  String? name  = stdin.readLineSync();
  print("The entered name is ${name}");
}

```


### Integer User Input

You can take integer input to get a numeric value from the user without the decimal point. E.g. 10, 100, -800 etc.

```
import 'dart:io';

void main() {
  print("Enter number:");
  int? number = int.parse(stdin.readLineSync()!);
  print("The entered number is ${number}");
}

```


### Floating Point User Input

You can use float input if you want to get a numeric value from the user with the decimal point. E.g. 10.5, 100.5, -800.9 etc.

```
import 'dart:io';

void main() {
  print("Enter a floating number:");
  double number = double.parse(stdin.readLineSync()!);
  print("The entered num is $number");
}

```


## String in Dart 
**String** helps you to store text based data. In String, you can represent your name, address, or complete book. It holds a series or sequence of characters – letters, numbers, and special characters. You can use single or double, or triple quotes to represent String.

### **Example: String In Dart**

Single line String is written in single or double quotes, whereas multi-line strings are written in triple quotes. Here is an example of it:

```
void main() {   
   String text1 = 'This is an example of a single-line string.';   
   String text2 = "This is an example of a single line string using double quotes.";   
   String text3 = """This is a multiline line   
string using the triple-quotes.
This is tutorial on dart strings.
""";   
   print(text1);  
   print(text2);   
   print(text3);   
}

```


[Run Online](https://dartpad.dev/?id=c2023963b37b2664ea4b40650e1c0037)

### **String Concatenation**

You can combine one String with another string. This is called concatenation. In Dart, you can use the `+` operator or use **interpolation** to concatenate the String. Interpolation makes it easy to read and understand the code.

### **String Concatenation In Dart**

```
void main() {   
String firstName = "John";
String lastName = "Doe";
print("Using +, Full Name is "+firstName + " " + lastName+".");
print("Using interpolation, full name is $firstName $lastName.");  
  
}

```


[Run Online](https://dartpad.dev/?id=e4abbe14213951d7526cb280eddc47c2)

### **Properties Of String**

*   **codeUnits**: Returns an unmodifiable list of the UTF-16 code units of this string.
*   **isEmpty**: Returns true if this string is empty.
*   **isNotEmpty**: Returns false if this string is empty.
*   **length**: Returns the length of the string including space, tab, and newline characters.

### **String Properties Example In Dart**

```
void main() {
   String str = "Hi";
   print(str.codeUnits);   //Example of code units
   print(str.isEmpty);     //Example of isEmpty
   print(str.isNotEmpty);  //Example of isNotEmpty
   print("The length of the string is: ${str.length}");   //Example of Length
}

```


[Run Online](https://dartpad.dev/?id=e2fdfcfe0fcfbd11df3644acc24b531a)

### Methods Of String

*   **toLowerCase()**: Converts all characters in this string to lowercase.
*   **toUpperCase()**: Converts all characters in this string to uppercase.
*   **trim()**: Returns the string without any leading and trailing whitespace.
*   **compareTo()**: Compares this object to another.
*   **replaceAll()**: Replaces all substrings that match the specified pattern with a given value.
*   **split()**: Splits the string at matches of the specified delimiter and returns a list of substrings.
*   **toString()**: Returns a string representation of this object.
*   **substring()**: Returns the text from any position you want.
*   **codeUnitAt()**: Returns the 16-bit UTF-16 code unit at the given index.

### **String Methods Example In Dart**

Here you will see various string methods that can help your work a lot better and faster.

### **Converting String To Uppercase and Lowercase**

You can convert your text to lower case using .toLowerCase() and convert to uppercase using .toUpperCase() method.

```
//Example of toUpperCase() and toLowerCase()
void main() { 
   String address1 = "Florida"; // Here F is capital
   String address2 = "TexAs"; // Here T and A are capital
   print("Address 1 in uppercase: ${address1.toUpperCase()}"); 
   print("Address 1 in lowercase: ${address1.toLowerCase()}"); 
   print("Address 2 in uppercase: ${address2.toUpperCase()}"); 
   print("Address 2 in lowercase: ${address2.toLowerCase()}"); 
}

```


[Run Online](https://dartpad.dev/?id=13ba9115b8702616179459da7c189cbe)

### **Trim String In Dart**

Trim is helpful when removing leading and trailing spaces from the text. This trim method will remove all the starting and ending spaces from the text. You can also use **trimLeft()** and **trimRight()** methods to remove space from left and right, respectively.

Info

**Note**: The trim() method in Dart doesn’t remove spaces in the middle.

```
//Example of trim()
void main() { 
  String address1 = " USA"; // Contain space at leading.
  String address2 = "Japan  "; // Contain space at trailing. 
  String address3 = "New Delhi"; // Contains space at middle.
  
  print("Result of address1 trim is ${address1.trim()}");
  print("Result of address2 trim is ${address2.trim()}");
  print("Result of address3 trim is ${address3.trim()}");
  print("Result of address1 trimLeft is ${address1.trimLeft()}");
  print("Result of address2 trimRight is ${address2.trimRight()}");
}

```


[Run Online](https://dartpad.dev/?id=9ce2e4517d297d4f22c9c055917c2617)

### **Compare String In Dart**

In Dart, you can compare two strings. It will give the result 0 when two texts are equal, 1 when the first String is greater than the second, and -1 when the first String is smaller than the second.

```
//Example of compareTo()
void main() { 
   String item1 = "Apple"; 
   String item2 = "Ant"; 
   String item3 = "Basket"; 
   
   print("Comparing item 1 with item 2: ${item1.compareTo(item2)}"); 
   print("Comparing item 1 with item 3: ${item1.compareTo(item3)}"); 
   print("Comparing item 3 with item 2: ${item3.compareTo(item2)}"); 
} 

```


[Run Online](https://dartpad.dev/?id=964cfc29d289b6949283c4fc7ad846ea)

### **Replace String In Dart**

You can replace one value with another with the replaceAll(“old”, “new”) method in Dart. It will replace all the “old” words with “new”. Here in this example, this will replace milk with water.

```
//Example of replaceAll()
void main() { 
String text = "I am a good boy I like milk. Doctor says milk is good for health.";
  
String newText = text.replaceAll("milk", "water"); 
 
print("Original Text: $text");
print("Replaced Text: $newText");  
   
} 

```


[Run Online](https://dartpad.dev/?id=47f1cae2e9a0e2f4502947f486fbe260)

### **Split String In Dart**

You can use the dart split method if you want to split String by comma, space, or other text. It will help you to split String to list.

```
//Example of split()
void main() { 
  String allNames = "Ram, Hari, Shyam, Gopal";

  List<String> listNames = allNames.split(",");
  print("Value of listName is $listNames");

  print("List name at 0 index ${listNames[0]}");
  print("List name at 1 index ${listNames[1]}");
  print("List name at 2 index ${listNames[2]}");
  print("List name at 3 index ${listNames[3]}");
   
} 

```


[Run Online](https://dartpad.dev/?id=e2084d37c1c4153c687157f0ab528731)

### **ToString In Dart**

In dart, toString() represents String representation of the value/object.

```
//Example of toString()
void main() { 
int number = 20;     
String result = number.toString(); 
  
print("Type of number is ${number.runtimeType}");  
print("Type of result is ${result.runtimeType}");  
    
}   

```


[Run Online](https://dartpad.dev/?id=85c061d07c69063fb819da5042ae9f03)

### **SubString In Dart**

You can use substring in Dart when you want to get a text from any position.

```
//Example of substring()
void main() { 
   String text = "I love computer"; 
   print("Print only computer: ${text.substring(7)}"); // from index 6 to the last index 
   print("Print only love: ${text.substring(2,6)}");// from index 2 to the 6th index 
} 

```


[Run Online](https://dartpad.dev/?id=e9b00023c94645700208883bf320aa39)

### **Reverse String In Dart**

If you want to reverse a String in Dart, you can reverse it using a different solution. One solution is here.

```
void main() { 
  String input = "Hello"; 
  print("$input Reverse is ${input.split('').reversed.join()}"); 
} 

```


[Run Online](https://dartpad.dev/?id=bdc13769cc0522c03ae999a6db4330a3)

### **How To Capitalize First Letter Of String In Dart**

If you want to capitalize the first letter of a String in Dart, you can use the following code.

```
//Example of capitalize first letter of String
void main() { 
  String text = "hello world"; 
  print("Capitalized first letter of String: ${text[0].toUpperCase()}${text.substring(1)}"); 
} 

```


[Run Online](https://dartpad.dev/?id=f0f335372ad3bad70a651a5e8967500b)


## Conditions in Dart 

With conditions, you can control the flow of the dart program. 

### Types Of Condition

You can use following conditions to control the flow of your program.

*   **If Condition**
*   **If-Else Condition**
*   **If-Else-If Condition**
*   **Switch case**

### **If Condition**

The easy and most common way of controlling the flow of a program is through the use of an _if statement_. If statement allow us to execute a code block when the given condition is true. Conditions evaluate boolean values.

### **Syntax**

```
if(condition) {
    Statement 1;
    Statement 2;
       .
       .
    Statement n;
}

```


### **Example Of If Condition**

It prints whether the person is a voter. If the person’s age is greater and equal to 18, it will print, You are a voter.

```
void main()
{
    var age = 20;
    
    if(age >= 18){
      print("You are voter.");
    }
}

```


[Run Online](https://dartpad.dev/?id=6d8cac25d23cfd6e3d344ea3d7d551f6)

### **If-Else Condition**

If the result of the condition is true, then the body of the if-condition is executed. Otherwise, the body of the else-condition is executed.

### **Syntax**

```
if(condition){
statements;
}else{
statements;
}

```


### **Example Of If-Else Condition**

Dart program prints whether the person is a voter or not based on age.

```
void main(){
        int age = 12;
        if(age >= 18){
            print("You are voter.");
        }else{
            print("You are not voter.");
        }
}

```


[Run Online](https://dartpad.dev/?id=976ee1d061eb24ba3ce26688bec33f37)

### **Condition Based On Boolean Value**

If the married status is false, it prints you are single; otherwise, it will print you are married.

```
void main(){
        bool isMarried = false;
        if(isMarried){
            print("You are married.");
        }else{
            print("You are single.");
        }
}

```


[Run Online](https://dartpad.dev/?id=419e922bfb5d57445ee39b0fd5abfb2c)

### **If-Else-If Condition**

When you have multiple if conditions, then you can use if-else-if. You can learn more in the example below. When you have more than two conditions, you can use if, else if, else in dart.

### **Syntax**

```
if(condition1){
statements1;
}else if(condition2){
statements2;
}else if(condition3){
statements3;
}
.
.
.
else(conditionN){
statementsN;
}

```


### **Example Of If-Else-If Condition**

This program prints the month name based on the numeric value of that month. You will get a different result if you change the number of month.

```
void main() {
  int noOfMonth = 5;

  // Check the no of month
  if (noOfMonth == 1) {
    print("The month is jan");
  } else if (noOfMonth == 2) {
    print("The month is feb");
  } else if (noOfMonth == 3) {
    print("The month is march");
  } else if (noOfMonth == 4) {
    print("The month is april");
  } else if (noOfMonth == 5) {
    print("The month is may");
  } else if (noOfMonth == 6) {
    print("The month is june");
  } else if (noOfMonth == 7) {
    print("The month is july");
  } else if (noOfMonth == 8) {
    print("The month is aug");
  } else if (noOfMonth == 9) {
    print("The month is sep");
  } else if (noOfMonth == 10) {
    print("The month is oct");
  } else if (noOfMonth == 11) {
    print("The month is nov");
  } else if (noOfMonth == 12) {
    print("The month is dec");
  } else {
    print("Invalid option given.");
  }
}

```


[Run Online](https://dartpad.dev/?id=6b8d479d070a1cdff239851785bf6935)

### **Find Greatest Number Among 3 Numbers**

Dart program, which finds the greatest number among three numbers.

```
void main(){
        int num1 = 1200;
        int num2 = 1000;
        int num3 = 150;

        if(num1 > num2  && num1 > num3){
            print("Num 1 is greater: i.e $num1");
        }
        if(num2 > num1 && num2 > num3){
           print("Num2 is greater: i.e $num2");
        }
        if(num3 > num1 && num3 > num2){
            print("Num3 is greater: i.e $num3");
        }
}

```


[Run Online](https://dartpad.dev/?id=9a8d5e29dc41c4b1713b920efae95cfa)

## Switch Case in Dart 

A Switch case is used to execute the code block based on the condition.

```
switch(expression) {
    case value1:
        // statements
        break;
    case value2:
        // statements
        break;
    case value3:
        // statements
        break;
    default:
       // default statements
}

```

**How does switch-case statement work in dart**

*   The **expression** is evaluated once and compared with each case value.
*   If **expression** matches with case value1, the statements of case value1 are executed. Similarly, case value 2 will be executed if the expression matches case value2. If the expression matches the case value3, the statements of case value3 are executed.
*   The **break** keywords tell dart to exit the switch statement because the statements in the case block are finished.
*   If there is no match, **default statements** are executed.

**Note**: You can use a Switch case as an alternative to the **if-else-if** condition.

### **Replace If Else If With Switch In Dart**

Here you can see the same program using **if else if** and **switch** in dart.

### **Example: Using If Else If**

This example prints the day name based on the numeric day of the week using a if else if.

```
void main(){
   var dayOfWeek = 5;
if (dayOfWeek == 1) {
        print("Day is Sunday.");
  }
else if (dayOfWeek == 2) {
       print("Day is Monday.");
     }
else if (dayOfWeek == 3) {
      print("Day is Tuesday.");
     }
else if (dayOfWeek == 4) {
        print("Day is Wednesday.");
     }
else if (dayOfWeek == 5) {
        print("Day is Thursday.");
   }
else if (dayOfWeek == 6) {
        print("Day is Friday.");
    }
else if (dayOfWeek == 7) {
        print("Day is Saturday.");
}else{
        print("Invalid Weekday.");
     }
}

```

[Run Online](https://dartpad.dev/?id=ee6d90177af379b0a6fc7917130249fc)

### **Example Of Switch Statement**

This example prints the day name based on the numeric day of the week using a switch case.

```
void main() {
  var dayOfWeek = 5;
  switch (dayOfWeek) {
    case 1:
        print("Day is Sunday.");
        break;
    case 2:
        print("Day is Monday.");
      break;
    case 3:
      print("Day is Tuesday.");
      break;
    case 4:
        print("Day is Wednesday.");
      break;
    case 5:
        print("Day is Thursday.");
      break;
    case 6:
        print("Day is Friday.");
      break;
    case 7:
        print("Day is Saturday.");
      break;
    default:
        print("Invalid Weekday.");
      break;
  }
}

```


[Run Online](https://dartpad.dev/?id=01f56818a1754280968c0b6546321478)

Info

**Note**: The syntax of switch statements is cleaner and much easier to read and write.

### **Switch Case On Strings**

You can also use a switch case with strings. This program prints information based on weather value.

```
void main() {
 const weather = "cloudy";

  switch (weather) {
    case "sunny":
        print("Its a sunny day. Put sunscreen.");
        break;
    case "snowy":
        print("Get your skis.");
      break;
    case "cloudy":
    case "rainy": 
      print("Please bring umbrella.");
      break;
    default:
        print("Sorry I am not familiar with such weather.");
      break;
  }
}

```

[Run Online](https://dartpad.dev/?id=ace41d17f7bc6b5f68a767cccc218000)

### **Switch Case On Enum**

An **[enum](https://dart-tutorial.com/object-oriented-programming/enum-in-dart/)** or enumeration is used for defining value according to you. You can define your own type with a finite number of options. Here is the syntax for defining enum.

### Syntax

```
enum enum_name { 
  constant_value1, 
  constant_value2, 
  constant_value3 
  }

```

### **Example of Switch Using Enum In Dart**

Enum plays well with switch statements. Let’s see an example using enum.

```
// define enum outside main function
enum Weather{ sunny, snowy, cloudy, rainy}
// main method
void main() {
 const weather = Weather.cloudy;
  
  switch (weather) {
    case Weather.sunny:
        print("Its a sunny day. Put sunscreen.");
        break;
    case Weather.snowy:
        print("Get your skis.");
      break;
    case Weather.rainy:
    case Weather.cloudy:
      print("Please bring umbrella.");
      break;
    default:
        print("Sorry I am not familiar with such weather.");
      break;
  }
}

```

[Run Online](https://dartpad.dev/?id=e954c4fc1f335d0c06cb66d6c4493392)

## Ternary Operator in Dart 

The ternary operator is like if-else statement. This is a one-liner replacement for the if-else statement. It is used to write a conditional expression, where based on the result of a boolean condition, one of the two values is selected.

### **Syntax**

```
condition ? exprIfTrue : exprIfFalse

```


**Note**: The ternary operator takes a condition and returns one of two values, depending upon the condition’s boolean value, i.e., true or false.

### **Ternary Operator Vs If Else**

We already learned if-else in dart. Let us see the same example using the if-else and ternary operator.

### Example Using If Else

This program finds greatest number between two numbers using if else.

```
void main() {
  int num1 = 10;
  int num2 = 15;
  int max = 0;
  if(num1> num2){
    max = num1;
  }else {
    max = num2;
  }
  print("The greatest number is $max");
}

```


[Run Online](https://dartpad.dev/?id=2a5b5e4364c0b8a960a7048dcf848d5c)

### **Example 1: Using Ternary Operator**

This program finds greatest number between two numbers using ternary operator.

```
void main() {
  int num1 = 10;
  int num2 = 15;
  int max = (num1 > num2) ? num1 : num2;
  print("The greatest number is $max");
}

```


[Run Online](https://dartpad.dev/?id=d8828e24baa9ad7c4e80cdda2fc9811a)

**Note**: Ternary operator makes if-else code much shorter and readable. If you have problems with ternary, you can always use if-else.

### **Example 2: Ternary Operator Dart**

If the selection value is 2 then it will set output as Apple otherwise, Banana.

```
void main() {
  var selection = 2;
  var output = (selection == 2) ? 'Apple' : 'Banana';
  print(output);
}

```


[Run Online](https://dartpad.dev/?id=4c3782133a8a3e3279dc14a1de2357f5)

### **Example 3 Ternary Operator Dart**

This is a dart program to print whether the person is a voter or not using a ternary operator.

```
void main() {
  var age = 18;
  var check = (age >= 18) ? 'You ara a voter.' : 'You are not a voter.';
  print(check);
}

```


[Run Online](https://dartpad.dev/?id=51c2bc6014a529fb0e8415e59c629fe5)

## For Loop in Dart 

This is the most common type of loop. You can use **for loop** to run a code block multiple times according to the condition. The syntax of for loop is:

```
for(initialization; condition; increment/decrement){
            statements;
}

```


*   Initialization is executed (one time) before the execution of the code block.
*   Condition defines the condition for executing the code block.
*   Increment/Decrement is executed (every time) after the code block has been executed.

### **Example 1: To Print 1 To 10 Using For Loop**

This example prints 1 to 10 using for loop. Here **int i = 1;** is initialization, **i<=10** is condition and **i++** is increment/decrement.

```
void main() {
  for (int i = 1; i <= 10; i++) {
    print(i);
  }
}

```


[Run Online](https://dartpad.dev/?id=264feb7ba11737142520e4b5f23351c0)

### **Example 2: To Print 10 To 1 Using For Loop**

This example prints 10 to 1 using for loop. Here **int i = 10;** is initialization, **i>=1** is condition and **`i--`** is increment/decrement.

```
void main() {
  for (int i = 10; i >= 1; i--) {
    print(i);
  }
}

```


[Run Online](https://dartpad.dev/?id=f82a4a43964c0086b4aab3e5894e4194)

### **Example 3: Print Name 10 Times Using For Loop**

This example prints the name 10 times using for loop. Based on the condition, the body of the loop executes 10 times.

```
void main() {
  for (int i = 0; i < 10; i++) {
    print("John Doe");
  }
}

```


[Run Online](https://dartpad.dev/?id=ee30fb7c24a66cfd219624363ceaba44)

### **Example 4: Display Sum of n Natural Numbers Using For Loop**

Here, the value of the **total** is **0** initially. Then, the for loop is iterated from **i = 1 to 100**. In each iteration, **i** is added to the **total**, and the value of **i** is increased by 1. Result is **1+2+3+….+99+100**.

```
void main(){

  int total = 0;
  int n = 100; // change as per required
  
  for(int i=1; i<=n; i++){
    total = total + i;
  }
  
  print("Total is $total");
  
}

```


[Run Online](https://dartpad.dev/?id=c2a8725e7265d0913de7df0457481fbe)

### **Example 5: Display Even Numbers Between 50 to 100 Using For Loop**

This program will print even numbers between 50 to 100 using for loop.

```
void main(){
  for(int i=50; i<=100; i++){
    if(i%2 == 0){
      print(i);
    }
  } 
}

```


[Run Online](https://dartpad.dev/?id=045b8c1efb218cc4b6a3faf5cda9ac7c)

### **Infinite Loop In Dart**

If the condition never becomes false in looping, it is called an infinite loop. It uses more resources on your computer. The task is done repeatedly until the memory runs out.

This program prints 1 to infinite because the condition is **i>=1**, which is always true with i++.

```
void main() {
  for (int i = 1; i >= 1; i++) {
    print(i);
  }
}

```


Info

**Note**: Infinite loops take your computer resources continuously, use more power, and slow your computer. So always check your loop before use.

## For Each Loop in Dart

The **for each** loop iterates over all list elements or variables. It is useful when you want to loop through **list/collection**. The syntax of for-each loop is:

```
collection.forEach(void f(value));

```


### **Example 1: Print Each Item Of List Using Foreach**

This will print each name of football players.

```
void main(){
  List<String> footballplayers=['Ronaldo','Messi','Neymar','Hazard'];
  footballplayers.forEach( (names)=>print(names));
}

```


[Run Online](https://dartpad.dev/?id=3546b6f86e5fa6d692259a57bb2b31c3)

### **Example 2: Print Each Total and Average Of Lists**

This program will print the total sum of all numbers and also the average value from the total.

```
void main(){
  List<int> numbers = [1,2,3,4,5];
  
  int total = 0;
  
   numbers.forEach( (num)=>total= total+ num);
  
  print("Total is $total.");
  
  double avg = total / (numbers.length);
  
  print("Average is $avg.");
  
}

```


[Run Online](https://dartpad.dev/?id=398279cbea47b32e742d90523ede34a8)

### **For In Loop In Dart**

There is also another for loop, i.e., **for in loop**. It also makes looping over the list very easily.

```
void main(){
    List<String> footballplayers=['Ronaldo','Messi','Neymar','Hazard'];

  for(String player in footballplayers){
    print(player);
  }
}

```


[Run Online](https://dartpad.dev/?id=5e76bb057666cf7c4e5c1cc3c45fa918)

### **How to Find Index Value Of List**

In dart, asMap method converts the list to a map where the keys are the index and values are the element at the index.

```
void main(){

List<String> footballplayers=['Ronaldo','Messi','Neymar','Hazard'];

footballplayers.asMap().forEach((index, value) => print("$value index is $index"));

}

```


[Run Online](https://dartpad.dev/?id=cc3495b4811d8ee0c52618ec6551614e)

### **Example 3: Print Unicode Value of Each Character of String**

This will split the name into Unicode values and then find characters from the Unicode value.

```
void main(){
  
String name = "John";
     
for(var codePoint in name.runes){
  print("Unicode of ${String.fromCharCode(codePoint)} is $codePoint.");
}
}

```


[Run Online](https://dartpad.dev/?id=72c0263e605c022d0134c4e58480f205)

## While Loop in Dart 

In **while loop**, the loop’s body will run until and unless the condition is true. You must write conditions first before statements. This loop checks conditions on every iteration. If the condition is true, the code inside {} is executed, if the condition is false, then the loop stops.

### Syntax

```
while(condition){  
       //statement(s);  
      // Increment (++) or Decrement (--) Operation;  
}  

```


*   A while loop evaluates the condition inside the parenthesis ().
*   If the condition is true, the code inside {} is executed.
*   The condition is re-checked until the condition is false.
*   When the condition is false, the loop stops.

### **Example 1: To Print 1 To 10 Using While Loop**

This program prints 1 to 10 using while loop.

```
void main() {
  int i = 1;
  while (i <= 10) {
    print(i);
    i++;
  }
}

```


[Run Online](https://dartpad.dev/?id=4bd92d159957b654e5f8e0703eb6a620)

Info

**Note**: Do not forget to increase the variable used in the condition. Otherwise, the loop will never end and becomes an infinite loop.

### **Example 2: To Print 10 To 1 Using While Loop**

This program prints 10 to 1 using while loop.

```
void main() {
  int i = 10;
  while (i >= 1) {
    print(i);
    i--;
  }
}

```


[Run Online](https://dartpad.dev/?id=d625da929c5550ba0f65397010922653)

### **Example 3: Display Sum of n Natural Numbers Using While Loop**

Here, the value of the total is 0 initially. Then, the while loop is iterated from **i = 1 to 100**. In each iteration, **i** is added to the total, and the value of **i** is increased by 1. Result is **1+2+3+….+99+100**.

```
void main(){

  int total = 0;
  int n = 100; // change as per required
  int i =1;

  while(i<=n){
    total = total + i;
    i++;
  }
  
  print("Total is $total");
  
}

```


[Run Online](https://dartpad.dev/?id=d7212f76e2c02a141c001b86136f92fd)

### **Example 4: Display Even Numbers Between 50 to 100 Using While Loop**

This program will print even numbers between 50 to 100 using while loop.

```
void main(){
  int i = 50;
  while(i<=100){
  if(i%2 == 0){
      print(i);
    }
    i++;
  }
}

```


[Run Online](https://dartpad.dev/?id=88474097465d8039d38c35f68f886a70)

## Do While Loop in Dart 

Do while loop is used to run a block of code multiple times. The loop’s body will be executed first, and then the condition is tested. The syntax of do while loop is:

```
do{
    statement1;
    statement2;
    .
    .
    .
    statementN;
}while(condition);

```


*   First, it runs statements, and finally, the condition is checked.
*   If the condition is true, the code inside {} is executed.
*   The condition is re-checked until the condition is false.
*   When the condition is false, the loop stops.

Info

**Note**: In a do-while loop, the statements will be executed at least once time, even if the condition is false. It is because the statement is executed before checking the condition.

### **Example 1: To Print 1 To 10 Using Do While Loop**

```
void main() {
  int i = 1;
  do {
    print(i);
    i++;
  } while (i <= 10);
}

```


[Run Online](https://dartpad.dev/?id=3ed5f1b22915886443ecc157480e6bbc)

### **Example 2: To Print 10 To 1 Using Do While Loop**

```
void main() {
  int i = 10;
  do {
    print(i);
    i--;
  } while (i >= 1);
}

```


[Run Online](https://dartpad.dev/?id=5f8af035a8fa74c794c82bbaa589d03a)

### **Example 3: Display Sum of n Natural Numbers Using Do While Loop**

Here, the value of the **total** is 0 initially. Then, the do-while loop is iterated from **i = 1 to 100**. In each iteration, **i** is added to the total, and the value of **i** is increased by 1. Result is **1+2+3+….+99+100**.

```
void main(){

  int total = 0;
  int n = 100; // change as per required
  int i =1;
  
  do{
  total = total + i;
    i++;
  }while(i<=n);
  
  print("Total is $total");
  
}

```


[Run Online](https://dartpad.dev/?id=491f3761c6e018e314945490efc86bfb)

### **When The Condition Is False**

Let’s make one condition false and see the demo below. **Hello** got printed if the condition is false.

```
void main(){

  int number = 0;
  
  do{
  print("Hello");
  number--;
  }while(number >1);
  
}

```


[Run Online](https://dartpad.dev/?id=7c3c2a8a4e750a3f2a8169f86d5d04e4)

## Break and Continue in Dart 

In this tutorial, you will learn about the **break and continue** in dart. While working on loops, we need to skip some elements or terminate the loop immediately without checking the condition. In such a situation, you can use the break and continue statement.

### **Break Statement**

Sometimes you will need to break out of the loop immediately without checking the condition. You can do this using break statement.

The break statement is used to exit a loop. It stops the loop immediately, and the program’s control moves outside the loop. Here is syntax of break:

### **Example 1: Break In Dart For Loop**

Here, the loop condition is true until the value of i is less than or equal to 10. However, the break says to go outside the loop when the value of i becomes 5.

```
void main() {
  for (int i = 1; i <= 10; i++) {
    if (i == 5) {
      break;
    }
    print(i);
  }
}

```


[Run Online](https://dartpad.dev/?id=50ac9046a365fef6dde49b5db51619df)

### **Example 2: Break In Dart Negative For Loop**

Here, the loop condition is true until the value of i is more than or equal to 1. However, the break says to go outside the loop when the value of i becomes 7.

```
void main() {
  for (int i = 10; i >= 1; i--) {
    if (i == 7) {
      break;
    }
    print(i);
  }
}

```


[Run Online](https://dartpad.dev/?id=3018972104eb8b763dfc0963ab20f378)

### **Example 3: Break In Dart While Loop**

Here, this while loop condition is true until the value of i is less than or equal to 10. However, the break says to go outside the loop when the value of i becomes 5.

```
void main() {
 int i =1;
 while(i<=10){
  print(i);
   if (i == 5) {
      break;
    }
    i++;
 }
}

```


[Run Online](https://dartpad.dev/?id=fc56b90939f7b2f0071143cc57108b94)

### **Example 4: Break In Switch Case**

As we already learn in dart switch case, it is important to add **break** keyword in switch statement. This example prints the month name based on the number of the month using a switch case.

```
void main() {
  var noOfMoneth = 5;
  switch (noOfMoneth) {
    case 1:
      print("Selected month is January.");
      break;
    case 2:
      print("Selected month is February.");
      break;
    case 3:
      print("Selected month is march.");
      break;
    case 4:
      print("Selected month is April.");
      break;
    case 5:
      print("Selected month is May.");
      break;
    case 6:
      print("Selected month is June.");
      break;
    case 7:
      print("Selected month is July.");
      break;
    case 8:
      print("Selected month is August.");
      break;
    case 9:
      print("Selected month is September.");
      break;
    case 10:
      print("Selected month is October.");
      break;
    case 11:
      print("Selected month is November.");
      break;
    case 12:
      print("Selected month is December.");
      break;
    default:
      print("Invalid month.");
      break;
  }
}

```


[Run Online](https://dartpad.dev/?id=089433333e62977d5957c4b3d2882930)

### **Continue Statement**

Sometimes you will need to skip an iteration for a specific condition. You can do this utilizing continue statement.

The continue statement skips the current iteration of a loop. It will bypass the statement of the loop. It does not terminate the loop but rather continues with the next iteration. Here is the syntax of continue statement:

### **Example 1: Continue In Dart**

Here, the loop condition is true until the value of i is less than or equal to 10. However, the continue says to go to the next iteration of the loop when the value of i becomes 5.

```
void main() {
  for (int i = 1; i <= 10; i++) {
    if (i == 5) {
      continue;
    }
    print(i);
  }
}

```


[Run Online](https://dartpad.dev/?id=c5f2878678e363a80626ba578c53bdb9)

### **Example 2: Continue In For Loop Dart**

Here, the loop condition is true until the value of i is more than or equal to 1. However, the continue says to go to the next iteration of the loop when the value of i becomes 4.

```
void main() {
  for (int i = 10; i >= 1; i--) {
    if (i == 4) {
      continue;
    }
    print(i);
  }
}

```


[Run Online](https://dartpad.dev/?id=822da2a7cb4e2b6fd4bae2c249c7aa52)

### **Example 3: Continue In Dart While Loop**

Here, this while loop condition is true until the value of i is less than or equal to 10. However, the continue says to go to the next iteration of the loop when the value of i becomes 5.

```
void main() {
  int i = 1;
  while (i <= 10) {
    if (i == 5) {
      i++;
      continue;
    }
    print(i);
    i++;
  }
}

```


[Run Online](https://dartpad.dev/?id=74b1837417fe0f7f53207072e58f45d1)

## Exception Handling in Dart 
### **Exception In Dart**

An exception is an error that occurs at runtime during program execution. When the exception occurs, the flow of the program is interrupted, and the program terminates abnormally. There is a high chance of crashing or terminating the program when an exception occurs. Therefore, to save your program from crashing, you need to catch the exception.

Info

**Note**: If you are attempting a task that might result in an error, it’s a good habit to use the try-catch statement.

### **Syntax**

```
try {
// Your Code Here
  }
catch(ex){
// Exception here
}

```


### **Try & Catch In Dart**

**Try** You can write the logical code that creates exceptions in the try block.

**Catch** When you are uncertain about what kind of exception a program produces, then a catch block is used. It is written with a try block to catch the general exception.

### **Example 1: Try Catch In Dart**

In this example, you will see how to handle the exception using the try-catch block.

```
void main() {   
   int a = 18;   
   int b = 0;   
   int res;    
     
   try {    
      res = a ~/ b;
      print("Result is $res");   
   }    
    // It returns the built-in exception related to the occurring exception  
   catch(ex) {   
      print(ex);   
    }   
}  

```


[Run Online](https://dartpad.dev/?id=fbe990056aa6798dd04a0c4d1cd38dc3)

### **Finally In Dart Try Catch**

The **finally** block is always executed whether the exceptions occur or not. It is optional to include the final block, but if it is included, it should be after the try and catch block is over.

**On** block is used when you know what types of exceptions are produced by the program.

### **Syntax**

```
try {
.....
}
on Exception1 {
....
}
catch Exception2 {
....
}
finally {
// code that should always execute whether an exception or not.
}

```


### **Example 2: Finally In Dart Try Catch**

In this example, you will see how to handle the exception using the try-catch block with the finally block.

```
void main() {
  int a = 12;
  int b = 0;
  int res;
  try {
    res = a ~/ b;
  } on UnsupportedError {
    print('Cannot divide by zero');
  } catch (ex) {
    print(ex);
  } finally {
    print('Finally block always executed');
  }
}

```


[Run Online](https://dartpad.dev/?id=76649da1be9329e5adb737ab6537b02e)

### **Throwing An Exception**

The throw keyword is used to raise an exception explicitly. A raised exception should be handled to prevent the program from exiting unexpectedly.

### **Syntax**

```
throw new Exception_name() 

```


### **Example 3: Throwing An Exception**

In this example, you will see how to throw an exception using the throw keyword.

```
void main() {
  try {
    check_account(-10);
  } catch (e) {
    print('The account cannot be negative');
  }
}

void check_account(int amount) {
  if (amount < 0) {
    throw new FormatException(); // Raising explanation externally
  }
}

```


[Run Online](https://dartpad.dev/?id=bf9e42c2a20df5759490c0e7ee5b1d27)

### **Why Is Exception Handling Needed?**

Exceptions provide the means to separate the details of what to do when something out of the ordinary happens from the main logic of a program. Therefore, exceptions must be handled to prevent the application from unexpected termination. Here are some reasons why exception handling is necessary:

*   To avoid abnormal termination of the program.
*   To avoid an exception caused by logical error.
*   To avoid the program from falling apart when an exception occurs.
*   To reduce the vulnerability of the program.
*   To maintain a good user experience.
*   To try providing aid and some debugging in case of an exception.

### **How To Create Custom Exception In Dart**

As you go advance, you need to create your exception; Dart enables you to create your exception.

### **Syntax**

```
class YourExceptionClass implements Exception{
  // constructors, variables & methods
}

```


### **Example 4: How to Create & Handle Exception**

This program throws an exception when a student’s mark is negative. You will understand **implements** in the object-oriented programming section.

```
class MarkException implements Exception {
  String errorMessage() {
    return 'Marks cannot be negative value.';
  }
}

void main() {
  try {
    checkMarks(-20);
  } catch (ex) {
    print(ex.toString());
  }
}

void checkMarks(int marks) {
  if (marks < 0) throw MarkException().errorMessage();
}

```


[Run Online](https://dartpad.dev/?id=38e624859b1671f840556ce827140079)

### **Example 5: How to Create & Handle Exception**

This program throws an exception when you find the square root of a negative number.

```
import 'dart:math';

// custom exception class
class NegativeSquareRootException implements Exception {
  @override
  String toString() {
    return 'Sqauare root of negative number is not allowed here.';
  }
}

// get square root of a positive number
num squareRoot(int i) {
  if (i < 0) {
    // throw `NegativeSquareRootException` exception
    throw NegativeSquareRootException();
  } else {
    return sqrt(i);
  }
}

void main() {
  try {
    var result = squareRoot(-4);

    print("result: $result");
  } on NegativeSquareRootException catch (e) {
    print("Oops, Negative Number: $e");
  } catch (e) {
    print(e);
  } finally {
    print('Job Completed!');
  }
}

```


[Run Online](https://dartpad.dev/?id=10e7acfcc31f524a1e7d45d2b768df36)

## Functions in Dart 

**Functions** are the block of code that performs a specific task. They are created when some statements are repeatedly occurring in the program. The function helps reusability of the code in the program.

**Note**: The main objective of the function is **DRY(Don’t Repeat Yourself)**.

### **Function Advantages**

*   Avoid Code Repetition
*   Easy to divide the complex program into smaller parts
*   Helps to write a clean code

### **Syntax**

```
returntype functionName(parameter1,parameter2, ...){
  // function body
}

```


**Return type**: It tells you the function output type. It can be void, String, int, double, etc. If the function doesn’t return anything, you can use void as the return type.

**Function Name**: You can name functions by almost any name. Always follow a lowerCamelCase naming convention like void printName().

**Parameters**: Parameters are the input to the function, which you can write inside the bracket (). Always follow a lowerCamelCase naming convention for your function parameter.

### **Example 1: Function That Prints Name**

This is a simple program that prints name using function. The name of function is **printName()**.

```
// writing function outside main function.
void printName(){
  print("My name is Raj Sharma. I am from function.");
}
// this is our main function.
void main(){
  printName();
}

```


[Run Online](https://dartpad.dev/?id=1a1843e8361cdf3ff84007aa35a716dc)

### **Example 2: Function To Find Sum of Two Numbers**

This function finds the sum of two numbers. Here, the function accepts two parameters. i.e., **num1 and num2**, and the return type is void.

```
void add(int num1, int num2){
  int sum = num1 + num2;
   print("The sum is $sum");
}

void main(){
  add(10, 20);
}

```


[Run Online](https://dartpad.dev/?id=751cd393eb50f6be93ad6c5469275e49)

### **Example 3: Function That Find Simple Interest**

This function finds simple interest from principal, time and rate and display result.

```
// function that calculate interest
void calculateInterest(double principal, double rate, double time) {
  double interest = principal * rate * time / 100;
  print("Simple interest is $interest");
}

void main() {
  double principal = 5000;
  double time = 3;
  double rate = 3;
  calculateInterest(principal, rate, time);
}

```


[Run Online](https://dartpad.dev/?id=7650d5a07147369ce515a5ca809560b7)

### **Key Points**

*   In dart function are also objects.
*   You should follow the **lowerCamelCase** naming convention while naming function.
*   You should follow the **lowerCamelCase** naming convention while naming function parameters.

### **About lowerCamelCase**

Name should start with lower-case, and every second word’s first letter will be upper-case like num1, fullName, isMarried, etc. Technically, this naming convention is called lowerCamelCase.

### **Function Parameters Vs Arguments**

Many programmers are often confused about parameters and arguments. Let’s have a look at this example.

```
// Here num1 and num2 are parameters
void add(int num1, int num2){
  int sum;
  sum = num1 + num2;
   
  print("The sum is $sum");
}

void main(){
// Here 10 and 20 are arguments
  add(10, 20);
}

```


[Run Online](https://dartpad.dev/?id=b869453c5a183426f4e3414ce3f15ede)

*   Here in **add(int num1, int num2)**, num1 and num2 are parameters and in **add(10, 20)**, 10 and 20 are arguments.
*   Parameter is the name and data type you define as an input for your function.
*   Argument is the actual value that you passed in.

Info

**Note**: In dart, if you don’t write the return type of function. It will automatically understand.


## Types of Functions in Dart :: Dart Tutorial - Learn Dart Programming
### **Types Of Function**

**Functions** are the block of code that performs a specific task. Here are different types of functions:

*   No Parameter And No Return Type
*   Parameter And No Return Type
*   No Parameter And Return Type
*   Parameter And Return Type

### **Function With No Parameter And No Return Type**

In this function, you do not pass any parameter and expect no return type. Here is an example of it:

### **Example 1: No Parameter & No Return Type**

Here **printName()** is a function which prints name on screen.

```
void main() {
  printName();
}

void printName() {
  print("My name is John Doe.");
}

```


[Run Online](https://dartpad.dev/?id=d7894e31281ec69f141433769c81e7d7)

In this program, **printName()** is the function which has keyword **void**. It means it has **no return type**, and the empty pair of parentheses implies that there is **no parameter** that is passed to the function.

### **Example 2: No Parameter & No Return Type**

Here **printPrimeMinisterName()** is a function which prints prime minister name on screen.

```
void main() {
  print("Function With No Parameter and No Return Type");
  printPrimeMinisterName();
}

void printPrimeMinisterName() {
  print("John Doe.");
}

```


[Run Online](https://dartpad.dev/?id=220db13fab191bff038d75c3effafc63)

### **Function With Parameter And No Return Type**

In this function, you do pass the parameter and expect no return type. Here is an example of it:

### **Example 1: Parameter & No Return Type**

Here **printName(String name)** is a function which welcome person.

```
void main() {
  printName("John");
}

void printName(String name) {
  print("Welcome, ${name}.");
}

```


[Run Online](https://dartpad.dev/?id=ad0b462f855964a5832b9cca0a006456)

In this program, **printName(String name)** is the function which has keyword **void**. It means it has **no return type**, and the pair of parentheses is not empty but this time that suggests it to accept an **parameter**.

### **Example 2: Parameter & No Return Type**

Here **add(int a, int b)** is a function that finds and prints the sum of two numbers.

```
// This function add two numbers
void add(int a, int b) {
  int sum = a + b;
  print("The sum is $sum");
}

void main() {
  int num1 = 10;
  int num2 = 20;

  add(num1, num2);
}

```


[Run Online](https://dartpad.dev/?id=9b3295128019ab7b80fc78b0f0c03fbf)

### **Function With No Parameter And Return Type**

In this function, you do not pass any parameter but expect return type. Here is an example of it:

### **Example 1: No Parameter & Return Type**

Here **primeMinisterName()** is a function which returns prime minister name. In the entire program, anyone can use this function to find the name of the prime minister.

```
void main() {
// Function With No Parameter & Return Type
  String name = primeMinisterName();
  print("The Name from function is $name.");
}
String primeMinisterName() {
  return "John Doe";
}

```


[Run Online](https://dartpad.dev/?id=c96e8149702197004a330b4b558a048e)

In this program, **primeMinisterName()** is the function which has **String** keyword before function name, means it **return** String value, and the empty pair of parentheses suggests that there is **no parameter** that is passed to the function.

### **Example 2: No Parameter & Return Type**

Here **voterAge()** is a function which returns minimum voter age.

```
// Function With No Parameter & Return Type
void main() {
  int personAge = 17;

  if (personAge >= voterAge()) {
    print("You can vote.");
  } else {
    print("Sorry, you can't vote.");
  }
}

int voterAge() {
  return 18;
}

```


[Run Online](https://dartpad.dev/?id=0114d061a25e1e26b8d3bf105b24cb29)

### **Function With Parameter And Return Type**

In this function, you do pass the parameter and also expect return type. Here is an example of it:

### **Example 1: Parameter & Return Type**

Here **add(int a, int b)** is a function that returns its sum in integer. We can display results in our main function.

```
// this function add two numbers
int add(int a, int b) {
  int sum = a + b;
  return sum;
}

void main() {
  int num1 = 10;
  int num2 = 20;

  int total = add(num1, num2);
  print("The sum is $total.");
}

```


[Run Online](https://dartpad.dev/?id=f9631f623653b1990513c8e7698509e2)

In this program, **int add(int a, int b)** is the function with **int** as the return type, and the pair of parenthesis has two **parameters**, i.e., a and b.

### **Example 2: Parameter & Return Type**

Here **calculateInterest(double principal, double rate, double time)** is a function that returns its simple interest in double. We can display results in our main function.

```
// function that calculate interest
double calculateInterest(double principal, double rate, double time) {
  double interest = principal * rate * time / 100;
  return interest;
}

void main() {
  double principal = 5000;
  double time = 3;
  double rate = 3;
  double result = calculateInterest(principal, rate, time);
  print("The simple interest is $result.");
}

```


[Run Online](https://dartpad.dev/?id=da88ac059ff1947abe46bced02f0af0b)

**Note**: void is used for no return type as it is a non value-returning function.

### \*\*Complete Example \*\*

Here is the program, which includes all types of functions we studied earlier.

```
// parameter and return type
int add(int a, int b) {
  var total;
  total = a + b;
  return total;
}

// parameter and no return type
void mul(int a, int b) {
  var total;
  total = a * b;
  print("Multiplication is : $total");
}

// no parameter and return type
String greet() {
  String greet = "Welcome";
  return greet;
}

// no parameter and no return type
void greetings() {
  print("Hello World!!!");
}

void main() {
  var total = add(2, 3);
  print("Total sum: $total");
  mul(2, 3);
  var greeting = greet();
  print("Greeting: $greeting");
  greetings();
}

```


[Run Online](https://dartpad.dev/?id=acf8ce1d1d325f6783bbce80f7c6b14b)

## Function Parameter in Dart 
### **Parameter In Dart**

The parameter is the process of passing values to the function. The values passed to the function must match the number of parameters defined. A function can have any number of parameters.

```
// here a and b are parameters
void add(int a, int b) { 
} 

```


### **Positional Parameter In Dart**

In positional parameters, you must supply the arguments in the same order as you defined on parameters when you wrote the function. If you call the function with the parameter in the wrong order, you will get the wrong result.

### **Example 1: Use Of Positional Parameter**

In the example below, the function **printInfo** takes two parameters. You must pass the person’s name and gender in the same order. If you pass values in the wrong order, you will get the **wrong result**.

```
void printInfo(String name, String gender) {
  print("Hello $name your gender is $gender.");
}

void main() {
  // passing values in wrong order
  printInfo("Male", "John");

  // passing values in correct order
  printInfo("John", "Male");

}

```


[Run Online](https://dartpad.dev/?id=8d5bdeb2d1eae817658f9fd141b00655)

### **Example 2: Providing Default Value On Positional Parameter**

In the example below, function **printInfo** takes two positional parameters and one optional parameter. The title parameter is optional here. If the user doesn’t pass the title, it will automatically set the title value to **sir/ma’am**.

```
void printInfo(String name, String gender, [String title = "sir/ma'am"]) {
  print("Hello $title $name your gender is $gender.");
}

void main() {
  printInfo("John", "Male");
  printInfo("John", "Male", "Mr.");
  printInfo("Kavya", "Female", "Ms.");
}

```


[Run Online](https://dartpad.dev/?id=965979f3c88c980a0b7454b458f50eb5)

### **Example 3: Providing Default Value On Positional Parameter**

In the example below, function **add** takes two positional parameters and one optional parameter. The **num3** parameter is **optional** here with default value **0**.

```
void add(int num1, int num2, [int num3=0]){
   int sum;
  sum = num1 + num2 + num3;
   
   print("The sum is $sum");
}

void main(){
  add(10, 20);
  add(10, 20, 30);
}

```


[Run Online](https://dartpad.dev/?id=b59f4dbc5355d207ce289fd2593359a4)

### **Named Parameter In Dart**

Dart allows you to use named parameters to clarify the parameter’s meaning in function calls. **Curly braces {}** are used to specify named parameters.

### **Example 1: Use Of Named Parameter**

In the example below, function **printInfo** takes two named parameters. You can pass value in any order. You will learn about **?** in **null safety** section.

```
void printInfo({String? name, String? gender}) {
  print("Hello $name your gender is $gender.");
}

void main() {
  // you can pass values in any order in named parameters.
  printInfo(gender: "Male", name: "John");
  printInfo(name: "Sita", gender: "Female");
  printInfo(name: "Reecha", gender: "Female");
  printInfo(name: "Reecha", gender: "Female");
  printInfo(name: "Harry", gender: "Male");
  printInfo(gender: "Male", name: "Santa");
}

```


[Run Online](https://dartpad.dev/?id=6a8792f6f343fd5062b28bc83f3eddfd)

### **Example 2: Use Of Required In Named Parameter**

In the example below, function **printInfo** takes two named parameters. You can see a **required** keyword, which means you must pass the person’s name and gender. If you don’t pass it, it won’t work.

```
void printInfo({required String name, required String gender}) {
  print("Hello $name your gender is $gender.");
}

void main() {
  // you can pass values in any order in named parameters.
  printInfo(gender: "Male", name: "John");
  printInfo(gender: "Female", name: "Suju");
}

```


[Run Online](https://dartpad.dev/?id=b2ce48d6cd282a9d1113b59b0d71c976)

Info

**Note**: You can pass the value in any order in the named parameter. **?** is used to remove null safety, which we will discuss in the coming chapter.

### **Optional Parameter In Dart**

Dart allows you to use optional parameters to make the parameter optional in function calls. **Square braces \[\]** are used to specify optional parameters.

### **Example: Use Of Optional Parameter**

In the example below, function **printInfo** takes two **positional parameters** and one **optional parameter**. First, you must pass the person’s name and gender. The title parameter is optional here. Writing **\[String? title\]** makes **title** optional.

```
void printInfo(String name, String gender, [String? title]) {
  print("Hello $title $name your gender is $gender.");
}

void main() {
  printInfo("John", "Male");
  printInfo("John", "Male", "Mr.");
  printInfo("Kavya", "Female", "Ms.");
}

```


[Run Online](https://dartpad.dev/?id=ec0d52e0f1d15f7e9aeebe1a8f9bcb01)

## Anonymous Function in Dart 

This tutorial will teach you the anonymous function and how to use it. You already saw function like **main()**, **add()**, etc. These are the **named** functions, which means they have a certain name.

But not every function needs a name. If you remove the return type and the function name, the function is called **anonymous function**.

### **Syntax**

Here is the syntax of the anonymous function.

```
(parameterList){
// statements
}

```


### **Example 1: Anonymous Function In Dart**

In this example, you will learn to use an anonymous function to print all list items. This function invokes each fruit without having a function name.

```
void main() {
  const fruits = ["Apple", "Mango", "Banana", "Orange"];

  fruits.forEach((fruit) {
    print(fruit);
  });
}

```


[Run Online](https://dartpad.dev/?id=eed29975b352c0f1f61760dc0c0d6bfe)

### **Example 2: Anonymous Function In Dart**

In this example, you will learn to find the cube of a number using an anonymous function.

```
void main() {
// Anonymous function
  var cube = (int number) {
    return number * number * number;
  };

  print("The cube of 2 is ${cube(2)}");
  print("The cube of 3 is ${cube(3)}");
}

```


[Run Online](https://dartpad.dev/?id=b57bd7884e109904eaf227e53148c464)

## Arrow Function in Dart

Dart has a special syntax for the function body, which is only one line. The arrow function is represented by **\=>** symbol. It is a shorthand syntax for any function that has only one expression.

### **Syntax**

The syntax for the dart arrow function.

```
returnType functionName(parameters...) => expression;

```


**Note**: The arrow function is used to make your code short.**\=> expr** syntax is a shorthand for **{ return expr; }**.

### **Example 1: Simple Interest Without Arrow Function**

This program finds simple interest without using the arrow function.

```
// function that calculate interest
double calculateInterest(double principal, double rate, double time) {
  double interest = principal * rate * time / 100;
  return interest;
}

void main() {
  double principal = 5000;
  double time = 3;
  double rate = 3;

  double result = calculateInterest(principal, rate, time);
  print("The simple interest is $result.");
}

```


[Run Online](https://dartpad.dev/?id=7766c775f91c378bb5d0efec23ecb183)

### **Example 2: Simple Interest With Arrow Function**

This program finds simple interest using the arrow function.

```
// arrow function that calculate interest
double calculateInterest(double principal, double rate, double time) =>
    principal * rate * time / 100;

void main() {
  double principal = 5000;
  double time = 3;
  double rate = 3;

  double result = calculateInterest(principal, rate, time);
  print("The simple interest is $result.");
}

```


[Run Online](https://dartpad.dev/?id=657009baa484bbaac0bc4f92adb2f7f2)

### **Example 3: Simple Calculation Using Arrow Function**

This program finds the sum, difference, multiplication, and division of two numbers using the arrow function.

```
int add(int n1, int n2) => n1 + n2;
int sub(int n1, int n2) => n1 - n2;
int mul(int n1, int n2) => n1 * n2;
double div(int n1, int n2) => n1 / n2;

void main() {
  int num1 = 100;
  int num2 = 30;

  print("The sum is ${add(num1, num2)}");
  print("The diff is ${sub(num1, num2)}");
  print("The mul is ${mul(num1, num2)}");
  print("The div is ${div(num1, num2)}");
}

```


[Run Online](https://dartpad.dev/?id=516bd6e463ff93ead5edf7b69d7b3e2e)

## Scope in Dart 

The scope is a concept that refers to where values can be accessed or referenced. Dart uses curly braces **{}** to determine the scope of variables. If you define a variable inside curly braces, you can’t use it outside the curly braces.

### **Method Scope**

If you created variables inside the method, you can use them inside the method block but not outside the method block.

### **Example 1: Method Scope**

```
void main() {
  String text = "I am text inside main. Anyone can't access me.";
  print(text);
}

```


[Run Online](https://dartpad.dev/?id=1d97729350575e25c79cbdf8b5ef59b1)

In this program, **text** is a String type where you can access and print method only inside the main function but not outside the main function.

### **Global Scope**

You can define a variable in the global scope to use the variable anywhere in your program.

### **Example 1: Global Scope**

```
String global = "I am Global. Anyone can access me.";
void main() {
  print(global);
}

```


[Run Online](https://dartpad.dev/?id=5cb7155e0cfe835bce865764a1da3674)

In this program, the variable named **global** is a top-level variable; you can access it anywhere in the program.

Info

**Note**: Define your variable as much as close **Local** as you can. It makes your code clean and prevents you from using or changing them where you shouldn’t.

### **Lexical Scope**

Dart is lexically scoped language, which means you can find the scope of variables with the help of **braces {}**.

## Math in Dart 

Math helps you to perform mathematical calculations efficiently. With dart math, you can **generate random number**, **find square root**, **find power of number**, or **round specific numbers**. To use math in dart, you must `import 'dart:math';`.

### **How To Generate Random Numbers In Dart**

This example shows how to generate random numbers from **0 - 9** and also **1 to 10**. After watching this example, you can generate a random number between your choices.

```
import 'dart:math';
void main()
{
Random random = new Random();
int randomNumber = random.nextInt(10); // from 0 to 9 included
print("Generated Random Number Between 0 to 9: $randomNumber");
  
int randomNumber2 = random.nextInt(10)+1; // from 1 to 10 included  
print("Generated Random Number Between 1 to 10: $randomNumber2"); 
}

```


[Run Online](https://dartpad.dev/?id=bc906521f231d51ec3c5a4ee81f9d4c4)

*   In this program, **random.nextInt(10)** function is used to generate a random number between **0 and 9** in which the value is stored in a variable **randomNumber**.
    
*   The **random.nextInt(10)+1** function is used to generate random number between **1 to 10** in which the value is stored in a variable **randomNumber2**.
    

### **Generate Random Number Between Any Number**

Use this formula to generate a random number between any numbers in the dart.

```
 min + Random().nextInt((max + 1) - min);

```


### **Example: Random Number In Dart Between 10 - 20**

This program generates random numbers between 10 to 20.

```
import 'dart:math';
void main()
{

int min = 10;
int max = 20; 

int randomnum = min + Random().nextInt((max + 1) - min);
  
print("Generated Random number between $min and $max is: $randomnum");  
}

```


[Run Online](https://dartpad.dev/?id=fcc351a04341474cbc963937ed860275)

### **Random Boolean And Double Value**

Here you will learn how to generate random boolean and double values in dart.

```
  Random().nextBool(); // return true or false
  Random().nextDouble(); // return 0.0 to 1.0

```


### **Example 1: Generate Random Boolean And Double Values**

This example below generate random and boolean value.

```
import 'dart:math';
void main()
{
double randomDouble = Random().nextDouble();
bool randomBool = Random().nextBool();
  
print("Generated Random double value is: $randomDouble");  
print("Generated Random bool value is: $randomBool");  
}

```


[Run Online](https://dartpad.dev/?id=d51f0a1dc4cf3a6afabd87510e089ae5)

### **Example 2: Generate a List Of Random Numbers In Dart**

This example will generate a list of 10 random numbers between 1 to 100.

```
import 'dart:math';
void main()
{
List<int> randomList = List.generate(10, (_) => Random().nextInt(100)+1); 
print(randomList);  
}

```


[Run Online](https://dartpad.dev/?id=773b8fe29b427e94cffebe3882f32634)

### **Useful Math Function In Dart**

You can use some useful math functions to perform your daily task with dart programming.


|Function Name|Output|Description               |
|-------------|------|--------------------------|
|pow(10,2)    |100   |10 to the power 2 is 10*10|
|max(10,2)    |10    |Maximum number is 10      |
|min(10,2)    |2     |Minimum number is 2       |
|sqrt(25)     |5     |Square root of 25 is 5    |


### **Example: Math In Dart**

This example below finds the power of a number, a minimum and maximum value between two numbers, and the square root of a number.

```
import 'dart:math';
void main()
{
  int num1 = 10;
  int num2 = 2;

  num powernum = pow(num1,num2);
  num maxnum = max(num1,num2);
  num minnum = min(num1,num2);
  num squareroot = sqrt(25); // Square root of 25
  
  print("Power is $powernum"); 
  print("Maximum is $maxnum"); 
  print("Minimum is $minnum"); 
  print("Square root is $squareroot"); 
  
}

```


[Run Online](https://dartpad.dev/?id=5f165f8153240f2ea69654d8ea283d7f)

*   In this program, **pow(num1, num2)** is a function where num1 is a digit and num2 is a power.
*   **max(num1,num2)** is a function which give the maximum number between num1 and num2.
*   **min(num1,num2)** is a function which give the mininum number between num1 and num2.
*   **sqrt(25)** is a function that gives the square root of 25.


## List in Dart 

If you want to store multiple values in the same variable, you can use **List**. List in dart is similar to **Arrays** in other programming languages. E.g. to store the names of multiple students, you can use a List. The List is represented by **Square Braces\[\].**

### **How To Create List**

You can create a List by specifying the initial elements in a square bracket. Square bracket **\[\]** is used to represent a List.

```
// Integer List
List<int> ages = [10, 30, 23];

// String List
List<String> names = ["Raj", "John", "Rocky"];

// Mixed List
var mixed = [10, "John", 18.8];

```

### **Types Of Lists**

*   Fixed Length List
*   Growable List \[**Mostly Used**\]

### **Fixed Length List**

The fixed-length Lists are defined with the specified length. You cannot change the size at runtime. This will create List of 5 integers with the value 0.

```
void main() {  
   var list = List<int>.filled(5,0);  
   print(list);  
}

```

[Run Online](https://dartpad.dev/?id=435b64ef1dc3a1956bec1f90f3524bfd)

Info

Note: You cannot add a new item to **Fixed Length List**, but you can change the values of List.

### **Growable List**

A List defined without a specified length is called Growable List. The length of the growable List can be changed in runtime.

```
void main() {  
   var list1 = [210,21,22,33,44,55];  
   print(list1);  
}  

```

[Run Online](https://dartpad.dev/?id=fcbb0ff5a18b58da07c651cb18a9f678)

### **Access Item Of List**

You can access the List item by **index**. Remember that the List index always starts with **0**.

```
void main() {
  var list = [210, 21, 22, 33, 44, 55];

  print(list[0]);
  print(list[1]);
  print(list[2]);
  print(list[3]);
  print(list[4]);
  print(list[5]);
}

```

[Run Online](https://dartpad.dev/?id=4df857aa907cc94bd39aa358efcccef9)

### **Get Index By Value**

You can also get the index by value.

```
void main() {
  var list = [210, 21, 22, 33, 44, 55];

  print(list.indexOf(22));
  print(list.indexOf(33));
}

```

[Run Online](https://dartpad.dev/?id=6ae37c408e11aab38a25f6c32678fa4e)

### **Find The Length Of The List**

You can find the length of List by using **.length** property.

```
void main(){  
   List<String> names = ["Raj", "John", "Rocky"];
   print(names.length);
 }

```

[Run Online](https://dartpad.dev/?id=e9ab9ed13874c12aee3f755626d6235e)

Info

Note: Remember that List **index** starts with **0** and length always starts with **1**.

### **Changing Values Of List**

You can also change the value of List. You can do it by **listName\[index\]=value;**. For more, see the example below.

```
void main(){  
   List<String> names = ["Raj", "John", "Rocky"];
   names[1] = "Bill";
   names[2] = "Elon";
   print(names);
}

```

[Run Online](https://dartpad.dev/?id=12055628434885a94d851cc4ef7e2dcd)

### **Mutable And Immutable List**

A mutable List means they can change after the declaration, and an immutable List means they can’t change after the declaration.

```
List<String> names = ["Raj", "John", "Rocky"]; // Mutable List
names[1] = "Bill"; // possible
names[2] = "Elon"; // possible
    
const List<String> names = ["Raj", "John", "Rocky"]; // Immutable List
names[1] = "Bill"; // not possible
names[2] = "Elon"; // not possible

```

### **List Properties In Dart**

*   **first**: It returns the first element in the List.
*   **last**: It returns the last element in the List.
*   **isEmpty**: It returns **true** if the List is empty and **false** if the List is not empty.
*   **isNotEmpty**: It returns **true** if the List is not empty and **false** if the List is empty.
*   **length**: It returns the length of the List.
*   **reversed**: It returns a List in reverse order.
*   **single**: It is used to check if the List has only one element and returns it.

### **Access First And Last Elements Of List**

You can access the first and last elements in the List by:

```
void main() {
   List<String> drinks = ["water", "juice", "milk", "coke"];
   print("First element of the List is: ${drinks.first}");
   print("Last element of the List is: ${drinks.last}");
}  

```

[Run Online](https://dartpad.dev/?id=a9e9571dc9be52e88985fd80b96d1143)

### **Check The List Is Empty Or Not**

You can also check List contain any elements inside it or not. It will give result either in **true** or in **false**.

```
void main() {
   List<String> drinks = ["water", "juice", "milk", "coke"];
   List<int>  ages = [];
   print("Is drinks Empty: "+drinks.isEmpty.toString());
   print("Is drinks not Empty: "+drinks.isNotEmpty.toString());
   print("Is ages Empty: "+ages.isEmpty.toString());
   print("Is ages not Empty: "+ages.isNotEmpty.toString());
   
}  

```

[Run Online](https://dartpad.dev/?id=48641b91ad78114471165aa2a7af7dc1)

### **Reverse List In Dart**

You can easily reverse List by using **.reversed** properties. Here is an example below:

```
void main() {
   List<String> drinks = ["water", "juice", "milk", "coke"];
   print("List in reverse: ${drinks.reversed}");
}  

```
[Run Online](https://dartpad.dev/?id=5501d43466e1b7c7c049b4dc323f7d9c)

### **Adding Item To List**

Dart provides four methods to insert the elements into the Lists. These methods are given below.



* Method: add()
  * Description: Add one element at a time and returns the modified List object.
* Method: addAll()
  * Description: Insert the multiple values to the given List, and each value is separated by the commas and enclosed with a square bracket ([]).
* Method: insert()
  * Description: Provides the facility to insert an element at a specified index position.
* Method: insertAll()
  * Description: Insert the multiple value at the specified index position.


### **Example 1: Add Item To List**

In this example below, we are adding an item to evenList using **add()** method.

```
void main() {  
    var evenList = [2,4,6,8,10];  
    print(evenList);  
    evenList.add(12);  
    print(evenList);  
}  

```

[Run Online](https://dartpad.dev/?id=6e9d51b33ef774c98bea789e5d6d5024)

### **Example 2: Add Items To List**

In this example below, we are adding items to evenList using **addAll()** method.

```
void main() {
  var evenList = [2, 4, 6, 8, 10];
  print(evenList);
  evenList.addAll([12, 14, 16, 18]);
  print(evenList);
}

```

[Run Online](https://dartpad.dev/?id=4574deeb6dbfa2a667d3ff67e34ad50f)

### **Example 3: Insert Item To List**

In this example below, we are adding an item to myList using **insert()** method.

```
void main() {
  List myList = [3, 4, 2, 5];
  print(myList);
  myList.insert(2, 15);
  print(myList);
}

```

[Run Online](https://dartpad.dev/?id=6ad3b5f29e6dcacfde34ddc923a0c2a8)

### \*\*Example 4: Insert Items To List \*\*

In this example below, we are adding items to myList using **insertAll()** method.

```
void main() {
  var myList = [3, 4, 2, 5];
  print(myList);
  myList.insertAll(1, [6, 7, 10, 9]);
  print(myList);
}
  

```

[Run Online](https://dartpad.dev/?id=30e5e6960d2e05d99c17b517e088532d)

### **Replace Range Of List**

You can also replace the range of the List. For more, see the example below.

```
void main() {
  var list = [10, 15, 20, 25, 30];
  print("List before updation: ${list}");
  list.replaceRange(0, 4, [5, 6, 7, 8]);
  print("List after updation using replaceAll() function : ${list}");
}

```

[Run Online](https://dartpad.dev/?id=422e4c7cb0305806ccd251e1b80acbd4)

### **Removing List Elements**


|Method       |Description                                                         |
|-------------|--------------------------------------------------------------------|
|remove()     |Removes one element at a time from the given List.                  |
|removeAt()   |Removes an element from the specified index position and returns it.|
|removeLast() |Remove the last element from the given List.                        |
|removeRange()|Removes the item within the specified range.                        |


### **Example 1: Removing List Item From List**

In this example below, we are removing item of List using **remove()** method.

```
void main() {
  var list = [10, 20, 30, 40, 50];
  print("List before removing element : ${list}");
  list.remove(30);
  print("List after removing element : ${list}");
}

```

[Run Online](https://dartpad.dev/?id=a9b5f5de3ed6f4715742a0bb82ed75ef)

### **Example 2: Removing List Item From List**

In this example below, we are removing item of List using **removeAt()** method.

```
void main() {
  var list = [10, 11, 12, 13, 14];
  print("List before removing element : ${list}");
  list.removeAt(3);
  print("List after removing element : ${list}");
}

```

[Run Online](https://dartpad.dev/?id=4eb32e9382bd8f43e4967d74dea459c5)

### **Example 3: Removing Last Item From List**

In this example below, we are removing last item of List using **removeLast()** method.

```
void main() {
  var list = [10, 20, 30, 40, 50];
  print("List before removing element:${list}");
  list.removeLast();
  print("List after removing last element:${list}");
}

```

[Run Online](https://dartpad.dev/?id=57bb1b31fd02a0c0fe220402d39dc9a2)

### **Example 4: Removing List Range From List**

In this example below, we are removing the range of items of List using **removeRange()** method.

```
void main() {
  var list = [10, 20, 30, 40, 50];
  print("List before removing element:${list}");
  list.removeRange(0, 3);
  print("List after removing range element:${list}");
}

```

[Run Online](https://dartpad.dev/?id=57e901f607226aac87e6ed3e5efe6425)

### **Loops In List**

You can use for loop, for each loop, or any other type of loop.

```
void main() {
  List<int> list = [10, 20, 30, 40, 50];
  list.forEach((n) => print(n));
}

```

[Run Online](https://dartpad.dev/?id=0d29000e7ff3fa97970ae3277b1ace8a)

### **Multiply All Value By 2 Of All List**

This example below multiply value of List item by 2.

```
void main() {
  List<int> list = [10, 20, 30, 40, 50];
  var douledList = list.map((n) => n * 2);

  print((douledList));
}

```


[Run Online](https://dartpad.dev/?id=206c821dfd78247b87f354a05ef128fa)

### **Combine Two Or More List In Dart**

You can combine two or more Lists in dart by using **spread** syntax.

```
void main() {
  List<String> names = ["Raj", "John", "Rocky"];
  List<String> names2 = ["Mike", "Subash", "Mark"];

  List<String> allNames = [...names, ...names2];
  print(allNames);
}

```

[Run Online](https://dartpad.dev/?id=b1c3e94a9ddbd9b981b8eb31384e3dc4)

### **Conditions In List**

You can also use conditions in List. Here **sad = false** so cart doesn’t contain **Beer** in it.

```
void main() {
  bool sad = false;
  var cart = ['milk', 'ghee', if (sad) 'Beer'];
  print(cart);
}
 

```

[Run Online](https://dartpad.dev/?id=7f5860b2b6ddb098be0b5de777ca1d5a)

### **Where In List Dart**

You can use where with List to filter specific items. Here in this example, even numbers are only filtered.

```
void main(){
List<int> numbers = [2,4,6,8,10,11,12,13,14];

List<int> even = numbers.where((number)=> number.isEven).toList(); 
print(even);
}

```


[Run Online](https://dartpad.dev/?id=0acad1be5fbeac37ba35b7d6089e99b8)

**Note**: Choose Lists if order matters. You can easily add items to the end. Searching can be slow when the List size is big.

## Set in Dart

Set is a unique collection of items. You cannot store duplicate values in the Set. It is unordered, so it can be faster than lists while working with a large amount of data. Set is useful when you need to store unique values without considering the order of the input. E.g., fruits name, months name, days name, etc. It is represented by **Curley Braces{}.**

**Note**: The list allows you to add **duplicate items**, but the Set doesn’t allow it.

### **Syntax**
```dart
Set <variable_type> variable_name = {};
```

### **How To Create A Set In Dart**

You can create a Set in Dart using the **Set** type annotation. 

```
void main(){
  Set<String> fruits = {"Apple", "Orange", "Mango"};
  print(fruits);
}

```


[Run Online](https://dartpad.dev/?id=a81291eb0617b7bd9db9d5f82d94838e)

### **Set Properties In Dart**


|Properties|Work                             |
|----------|---------------------------------|
|first     |To get first value of Set.       |
|last      |To get last value of Set.        |
|isEmpty   |Return true or false.            |
|isNotEmpty|Return true or false.            |
|length    |It returns the length of the Set.|


### **Example of Set Properties Dart**

This example finds the first and last element of the Set, checks whether it is empty or not, and finds its length.

```
void main() {
  // declaring fruits as Set
  Set<String> fruits = {"Apple", "Orange", "Mango", "Banana"};

  // using different properties of Set
  print("First Value is ${fruits.first}");
  print("Last Value is ${fruits.last}");
  print("Is fruits empty? ${fruits.isEmpty}");
  print("Is fruits not empty? ${fruits.isNotEmpty}");
  print("The length of fruits is ${fruits.length}");
}

```

### **Check The Available Value**

If you want to see whether the Set contains specific items or not, you can use the **contains** method, which returns true or false.

```
void main(){
  Set<String> fruits = {"Apple", "Orange", "Mango"};
  print(fruits.contains("Mango"));
  print(fruits.contains("Lemon"));
}

```


[Run Online](https://dartpad.dev/?id=e158381f766d9be511b06aa5780a0f3c)

### **Add & Remove Items In Set**

Like lists, you can add or remove items in a Set. To add items use **add()** method and to remove use **remove()** method.


|Method  |Description                  |
|--------|-----------------------------|
|add()   |Add one element to Set.      |
|remove()|Removes one element from Set.|


```
void main(){
 Set<String> fruits = {"Apple", "Orange", "Mango"};
  
  fruits.add("Lemon");
  fruits.add("Grape");
  
  print("After Adding Lemon and Grape: $fruits");
  
  fruits.remove("Apple");
  print("After Removing Apple: $fruits");
}

```


[Run Online](https://dartpad.dev/?id=5adb9c8bb832520d8cbeebb09b859f83)

### **Adding Multiple Elements**

You can use **addAll()** method to add multiple elements from the list to Set.


|Method  |Description                                 |
|--------|--------------------------------------------|
|addAll()|Insert the multiple values to the given Set.|


```
void main(){
 Set<int> numbers = {10, 20, 30};
  numbers.addAll([40,50]);
 print("After adding 40 and 50: $numbers");
}    

```


[Run Online](https://dartpad.dev/?id=a4c3327c1f7aba19407f61637e7dc71f)

### **Printing All Values In Set**

You can print all Set items by using loops. [Click here](https://dart-tutorial.com/conditions-and-loops/loops-in-dart/) if you want to learn loop in dart.

```
void main(){
 Set<String> fruits = {"Apple", "Orange", "Mango"};
  
 for(String fruit in fruits){
   print(fruit);
 }
}

```


[Run Online](https://dartpad.dev/?id=be626d8991c500692b39daac328d9a18)

### **Set Methods In Dart**

Some other helpful Set methods in dart.


|Method        |Description                                                       |
|--------------|------------------------------------------------------------------|
|clear()       |Removes all elements from the Set.                                |
|difference()  |Creates a new Set with the elements of this that are not in other.|
|elementAt()   |Returns the index value of element.                               |
|intersection()|Find common elements in two sets.                                 |


### **Clear Set In Dart**

In this example, you can see how to remove all items from the Set in dart.

```
void main() {
  Set<String> fruits = {"Apple", "Orange", "Mango"};
  // to clear all items
  fruits.clear();

  print(fruits);
}

```


[Run Online](https://dartpad.dev/?id=ff1f296632223f0bb4cec6a6903b071f)

### **Difference In Set**

In Dart, the difference method creates a new Set with the elements that are not in the other.

```
void main() {
  Set<String> fruits1 = {"Apple", "Orange", "Mango"};
  Set<String> fruits2 = {"Apple", "Grapes", "Banana"};

  final differenceSet = fruits1.difference(fruits2);

  print(differenceSet);
}

```


[Run Online](https://dartpad.dev/?id=92152b6f5447d0c18f8bf29e5c83c070)

### **Element At Method In Dart**

In Dart you can find the Set value by its index number. The index number starts with 0.

```
void main() {
  Set<String> days = {"Sunday", "Monday", "Tuesday"};
  // index starts from 0 so 2 means Tuesday
  print(days.elementAt(2));
}

```


[Run Online](https://dartpad.dev/?id=c590abf0c2bbbb7df6e0c3ac13cc9cda)

### **Intersection Method In Dart**

In Dart, the intersection method creates a new Set with the common elements in 2 Sets. Here Apple is available in both Sets.

```
void main() {
  Set<String> fruits1 = {"Apple", "Orange", "Mango"};
  Set<String> fruits2 = {"Apple", "Grapes", "Banana"};

  final intersectionSet = fruits1.intersection(fruits2);

  print(intersectionSet);
}

```


[Run Online](https://dartpad.dev/?id=dd1d9fea77619307a9de26282c02e369)

## Map in Dart 
In a Map, data is stored as keys and values. In Map, each key must be unique. They are similar to `HashMaps` and Dictionaries in other languages.

### **How To Create Map In Dart**

Here we are creating a Map for **String** and **String**. It means keys and values must be the type of String. You can create a Map of any kind as you like.

```
void main(){
Map<String, String> countryCapital = {
  'USA': 'Washington, D.C.',
  'India': 'New Delhi',
  'China': 'Beijing'
};
  print(countryCapital);
}

```


[Run Online](https://dartpad.dev/?id=c8ff56092d2128b0a80ae75cb14bc979)

Info

**Note**: Here **Usa**, **India**, and **China** are keys, and it must be **unique**.

### **Access Value From Key**

You can find the value of Map from its key. Here we are printing **Washington, D.C.** by its key, i.e., **USA**.

```
void main(){
Map<String, String> countryCapital = {
  'USA': 'Washington, D.C.',
  'India': 'New Delhi',
  'China': 'Beijing'
};
  print(countryCapital["USA"]);
}

```


[Run Online](https://dartpad.dev/?id=48d1e56c5b29d4a2cfe84f77f54e9c01)

### **Map Properties In Dart**


|Properties|Work                             |
|----------|---------------------------------|
|keys      |To get all keys.                 |
|values    |To get all values.               |
|isEmpty   |Return true or false.            |
|isNotEmpty|Return true or false.            |
|length    |It returns the length of the Map.|


### **Example Of Map Properties In Dart**

This example finds all keys/values of Map, the first and last element, checks whether it is empty or not, and finds its length.

```
void main() {
 
  Map<String, double> expenses = {
    'sun': 3000.0,
    'mon': 3000.0,
    'tue': 3234.0,
  };
  
  print("All keys of Map: ${expenses.keys}");
  print("All values of Map: ${expenses.values}");
  print("Is Map empty: ${expenses.isEmpty}");
  print("Is Map not empty: ${expenses.isNotEmpty}");
  print("Length of map is: ${expenses.length}");
}

```


[Run Online](https://dartpad.dev/?id=018e421ba69575f674d94eb5af45bc05)

### **Adding Element To Map**

If you want to add an element to the existing Map. Here is the way for you:

```
void main(){
Map<String, String> countryCapital = {
  'USA': 'Washington, D.C.',
  'India': 'New Delhi',
  'China': 'Beijing'
};
  // Adding New Item
  countryCapital['Japan'] = 'Tokio';
  print(countryCapital);
}

```


[Run Online](https://dartpad.dev/?id=b31bbfd3e49ccdf41cf07728939b18cc)

### **Updating An Element Of Map**

If you want to update an element of the existing Map. Here is the way for you:

```
void main(){
Map<String, String> countryCapital = {
  'USA': 'Nothing',
  'India': 'New Delhi',
  'China': 'Beijing'
};
  // Updating Item
  countryCapital['USA'] = 'Washington, D.C.';
  print(countryCapital);
}

```


[Run Online](https://dartpad.dev/?id=d8190e762e8d657a43490064763a4e0a)

### **Map Methods In Dart**

Some useful Map methods in dart.


|Properties            |Work                                                    |
|----------------------|--------------------------------------------------------|
|keys.toList()         |Convert all Maps keys to List.                          |
|values.toList()       |Convert all Maps values to List.                        |
|containsKey(‘key’)    |Return true or false.                                   |
|containsValue(‘value’)|Return true or false.                                   |
|clear()               |Removes all elements from the Map.                      |
|removeWhere()         |Removes all elements from the Map if condition is valid.|


### **Convert Maps Keys & Values To List**

Let’s convert keys and values of Map to List.

```
void main() {
 
  Map<String, double> expenses = {
    'sun': 3000.0,
    'mon': 3000.0,
    'tue': 3234.0,
  };
  
  // Without List
  print("All keys of Map: ${expenses.keys}");
  print("All values of Map: ${expenses.values}");
 
  // With List
  print("All keys of Map with List: ${expenses.keys.toList()}");
  print("All values of Map with List: ${expenses.values.toList()}");
  
}

```


[Run Online](https://dartpad.dev/?id=0c0c31b4de26e1fd50f12a254bbc5da8)

### **Check Map Contains Specific Key/Value Or Not?**

Let’s check whether the Map contains a specific key/value in it or not.

```
void main() {
 
  Map<String, double> expenses = {
    'sun': 3000.0,
    'mon': 3000.0,
    'tue': 3234.0,
  };
  
  // For Keys
  print("Does Map contain key sun: ${expenses.containsKey("sun")}");
  print("Does Map contain key abc: ${expenses.containsKey("abc")}");
 
  // For Values
  print("Does Map contain value 3000.0: ${expenses.containsValue(3000.0)}");
  print("Does Map contain value 100.0: ${expenses.containsValue(100.0)}");
  
}

```


[Run Online](https://dartpad.dev/?id=ce64c93cc951a8d969954a98e02052d1)

### **Removing Items From Map**

Suppose you want to remove an element of the existing Map. Here is the way for you:

```
void main(){
Map<String, String> countryCapital = {
  'USA': 'Nothing',
  'India': 'New Delhi',
  'China': 'Beijing'
};
  
  countryCapital.remove("USA");
  print(countryCapital);
}

```


[Run Online](https://dartpad.dev/?id=bcddb1eaa4fb7ec897fb3d4318c27e31)

### **Looping Over Element Of Map**

You can use any loop in Map to print all keys/values or to perform operations in its keys and values.

```
void main(){

  Map<String, dynamic> book = {
    'title': 'Misson Mangal',
    'author': 'Kuber Singh',
    'page': 233
  };
  
 // Loop Through Map
  for(MapEntry book in book.entries){
    print('Key is ${book.key}, value ${book.value}');
  }
}

```


[Run Online](https://dartpad.dev/?id=d51dfb383cc42c9099afdc500de70078)

### **Looping In Map Using For Each**

In this example, you will see how to use a loop to print all the keys and values in Map.

```
void main(){

  Map<String, dynamic> book = {
    'title': 'Misson Mangal',
    'author': 'Kuber Singh',
    'page': 233
  };
  
  
 // Loop Through For Each
  book.forEach((key,value)=> print('Key is $key and value is $value'));
  
}

```


[Run Online](https://dartpad.dev/?id=29f7e04ab59ce860fb034b69e0d7d075)

### **Remove Where In Dart Map**

In this example, you will see how to get students whose marks are greater or equal to 32 using where method.

```
void main() {
  Map<String, double> mathMarks = {
    "ram": 30,
    "mark": 32,
    "harry": 88,
    "raj": 69,
    "john": 15,
  };
  mathMarks.removeWhere((key, value) => value < 32);
  print(mathMarks);
}

```


[Run Online](https://dartpad.dev/?id=ed459a19dbd14d4dc99aee6771fe172e)

## Where in Dart :: Dart Tutorial - Learn Dart Programming
### **Where Dart**

You can use where in list, set, map to **filter specific items**. It returns a new list containing all the elements that satisfy the condition. This is also called **Where Filter** in dart. Let’s see the syntax below:

### Syntax

```
Iterable<E> where(
bool test(
E element
)
)

```


### **Example 1: Filter Only Odd Number From List**

In this example, you will get only odd numbers from a list.

```
void main() {
  List<int> numbers = [2, 4, 6, 8, 10, 11, 12, 13, 14];

  List<int> oddNumbers = numbers.where((number) => number.isOdd).toList();
  print(oddNumbers);
}

```


[Run Online](https://dartpad.dev/?id=c3c3e9ed5adad4ec4ae46886c26433b2)

### **Example 2: Filter Days Start With S**

In this example, you will get only days that start with alphabet s.

```
void main() {
  List<String> days = [
    "Sunday",
    "Monday",
    "Tuesday",
    "Wednesday",
    "Thursday",
    "Friday",
    "Saturday"
  ];

  List<String> startWithS =
      days.where((element) => element.startsWith("S")).toList();

  print(startWithS);
}

```


[Run Online](https://dartpad.dev/?id=a3b6fe72bb23b3a7ee06166e301ca371)

### **Example 3: Where Filter In Map**

In this example, you will get students whose marks are greater or equal to 32.

```
void main() {
  Map<String, double> mathMarks = {
    "ram": 30,
    "mark": 32,
    "harry": 88,
    "raj": 69,
    "john": 15,
  };

  mathMarks.removeWhere((key, value) => value < 32);

  print(mathMarks);
}

```


[Run Online](https://dartpad.dev/?id=3468132eab9dba6639a823cab27da514)

## Read File in Dart 
### Introduction To File Handling

File handling is an important part of any programming language. In this section, you will learn how to read the file in a dart programming language.

### Read File In Dart

Assume that you have a file named `test.txt` in the same directory of your dart program.

```
Welcome to test.txt file.
This is a test file.

```


Now, you can read this file using **File** class and **readAsStringSync()** method.

```
// dart program to read from file
import 'dart:io';

void main() {
  // creating file object
  File file = File('test.txt');
  // read file
  String contents = file.readAsStringSync();
  // print file
  print(contents);
}

```


### Get File Information

In this example below, you will learn how to get file information like file location, file size, and last modified time.

```
import 'dart:io';

void main() {
  // open file
  File file = File('test.txt');
  // get file location
  print('File path: ${file.path}');
  // get absolute path
  print('File absolute path: ${file.absolute.path}');
  // get file size
  print('File size: ${file.lengthSync()} bytes');
  // get last modified time
  print('Last modified: ${file.lastModifiedSync()}');
}

```


Info

**Note**: If you try to get information of a file that does not exist, then it will throw an exception.

### CSV File

A CSV (**Comma Separated Values**) file is a plain text file that contains data organized in a table format, where columns are separated by commas and rows are separated by line breaks. CSV files are used for:

*   Data exchange between different applications.
*   Data backup and restore.
*   Importing and exporting data from databases.
*   Automation of data processing tasks.

### Read CSV File In Dart

Assume that you have a CSV file named `test.csv` in the same directory of your dart program.

Now, you can read this file using **File** class and **readAsStringSync()** method. We will use **split()** method to split the string into a list of strings.

```
// dart program to read from csv file
import 'dart:io';

void main() {
  // open file
  File file = File('test.csv');
  // read file
  String contents = file.readAsStringSync();
  // split file using new line
  List<String> lines = contents.split('\n');
  // print file
  print('---------------------');
  for (var line in lines) {
    print(line);
  }
}

```


### Read Only Part Of File

You can read only part of file using **substring()** method. Here is an example to read only first 10 characters of file. Make sure that you have a file named **test.txt** in the same directory of your dart program.

```
Welcome to test.txt file
This is a test file.

```


```
// dart program to read from file
import 'dart:io';

void main() {
  // open file
  File file = new File('test.txt');
  // read only first 10 characters
  String contents = file.readAsStringSync().substring(0, 10);
  // print file
  print(contents);
}

```


### Read File From Specific Directory

To read a file from a specific directory, you need to provide the full path of the file. Here is an example to read file from a specific directory.

```
// dart program to read from file
import 'dart:io';

void main() {
  // open file
  File file = File('C:\\Users\\test.txt');
  // read file
  String contents = file.readAsStringSync();
  // print file
  print(contents);
}

```

## Write File in Dart 
### Introduction

In this section, you will learn how to write file in dart programming language by using **File** class and **writeAsStringSync()** method.

### Write File In Dart

Let’s create a file named **test.txt** in the same directory of your dart program and write some text in it.

```
// dart program to write to file
import 'dart:io';

void main() {
  // open file
  File file = File('test.txt');
  // write to file
  file.writeAsStringSync('Welcome to test.txt file.');
  print('File written.');
}

```


Info

**Note**: If you have already some content in **test.txt** file, then it will be removed and replaced with new content.

### Add New Content To Previous Content

You can use **FileMode.append** to add new content to previous content. Assume that **test.txt** file already contains some text.

```
Welcome to test.txt file.

```


Now, let’s add new content to it.

```
// dart program to write to existing file
import 'dart:io';

void main() {
  // open file
  File file =  File('test.txt');
  // write to file
  file.writeAsStringSync('\nThis is a new content.', mode: FileMode.append);
  print('Congratulations!! New content is added on top of previous content.');
}

```


### Write CSV File In Dart

In the example below, we will ask user to enter **name** and **phone** of 3 students and write it to a csv file named **students.csv**.

```
// dart program to write to csv file
import 'dart:io';

void main() {
  // open file
  File file = File("students.csv");
  // write to file
  file.writeAsStringSync('Name,Phone\n');
  for (int i = 0; i < 3; i++) {
    // user input name
    stdout.write("Enter name of student ${i + 1}: ");
    String? name = stdin.readLineSync();
    stdout.write("Enter phone of student ${i + 1}: ");
    // user input phone
    String? phone = stdin.readLineSync();
    file.writeAsStringSync('$name,$phone\n', mode: FileMode.append);
  }
  print("Congratulations!! CSV file written successfully.");
}

```


**students.csv** file will look like this:

```
Name,Phone
John,1234567890
Mark,0123456789
Elon,0122112322

```


Info

**Note**: You can create any type of file using **writeAsStringSync()** method. For example, **.html**, **.json**, **.xml**, etc.

## Delete File in Dart 
### Introduction

In this section, you will learn how to delete file in dart programming language using **File** class and **deleteSync()** method.

### Delete File In Dart

Assume that you have a file named **test.txt** in the same directory of your dart program. Now, let’s delete it.

```
// dart program to delete file
import 'dart:io';

void main() {
  // open file
  File file = File('test.txt');
  // delete file
  file.deleteSync();
  print('File deleted.');
}

```


Info

**Note**: If you try to delete a file that does not exist, then it will throw an exception.

### Delete File If Exists

You can use **File.existsSync()** method to check if a file exists or not. If it exists, then you can delete it.

```
// dart program to delete file if exists
import 'dart:io';

void main() {
  // open file
  File file = File('test.txt');
  // check if file exists
  if (file.existsSync()) {
    // delete file
    file.deleteSync();
    print('File deleted.');
  } else {
    print('File does not exist.');
  }
}

```

## OOP in Dart 

**Object-oriented programming (OOP)** is a programming method that uses objects and their interactions to design and program applications. It is one of the most popular programming paradigms and is used in many programming languages, such as Dart, Java, C++, Python, etc.

In **OOP**, an object can be anything, such as a person, a bank account, a car, or a house. Each object has its attributes (or properties) and behavior (or methods). For example, a person object may have the attributes **name**, **age** and **height**, and the behavior **walk** and **talk**.

### **Advantages**

*   It is easy to understand and use.
*   It increases reusability and decreases complexity.
*   The productivity of programmers increases.
*   It makes the code easier to maintain, modify and debug.
*   It promotes teamwork and collaboration.
*   It reduces the repetition of code.

### **Features Of OOP**

1.  Class
2.  Object
3.  Encapsulation
4.  Inheritance
5.  Polymorphism
6.  Abstraction

Info

Note: The main purpose of OOP is to break complex problems into smaller objects. You will learn all these OOPs features later in this dart tutorial.

### **Key Points**

*   Object Oriented Programming (OOP) is a programming paradigm that uses objects and their interactions to design and program applications.
*   OOP is based on objects, which are data structures containing data and methods.
*   OOP is a way of thinking about programming that differs from traditional procedural programming.
*   OOP can make code more modular, flexible, and extensible.
*   OOP can help you to understand better and solve problems.

## Class in Dart 

In object-oriented programming, a class is a blueprint for creating objects. A class defines the properties and methods that an object will have. For example, a class called **Dog** might have properties like **breed**, **color** and methods like **bark**, **run**.

### **Declaring Class In Dart**

You can declare a class in dart using the **class** keyword followed by class name and braces {}. It’s a good habit to write class name in **PascalCase**. For example, **Employee**, **Student**, **QuizBrain**, etc.

### **Syntax**

```
class ClassName {
// properties or fields
// methods or functions
}

```


In the above syntax:

*   The **class** keyword is used for defining the class.
*   **ClassName** is the name of the class and must start with capital letter.
*   Body of the class consists of **properties** and **functions**.
*   **Properties** are used to store the data. It is also known as **fields** or **attributes**.
*   **Functions** are used to perform the operations. It is also known as **methods**.

### **Example : Declaring A Class In Dart**

In this example below, there is class **Animal** with three properties: **name**, **numberOfLegs**, and **lifeSpan**. The class also has a method called **display**, which prints out the values of the three properties.

```
class Animal {
  String? name;
  int? numberOfLegs;
  int? lifeSpan;

  void display() {
    print("Animal name: $name.");
    print("Number of Legs: $numberOfLegs.");
    print("Life Span: $lifeSpan.");
  }
}

```

**Note: This program will not print anything** because we have not created any object of the class. You will learn about the **object** later. The **?** is used for null safety. You will also learn about **null safety** later.

### **Key Points**

*   The class is declared using the **class** keyword.
*   The class is a blueprint for creating objects.
*   The class body consists of properties and methods.
*   The properties are also known as fields, attributes, or data members.
*   The methods are also known as behaviors, or member functions.


## Object in Dart 

**In object-oriented programming**, an object is a self-contained unit of code and data. Objects are created from templates called classes. An object is made up of properties(variables) and methods(functions). An object is an instance of a class.

**For example**, a bicycle object might have attributes like color, size, and current speed. It might have methods like changeGear, pedalFaster, and brake.

Info

**Note**: To create an object, you must create a class first. It’s a good practice to declare the object name in lower case.

### **Instantiation**

In object-oriented programming, instantiation is the process of creating an instance of a class. In other words, you can say that instantiation is the process of creating an object of a class. For example, if you have a class called **Bicycle**, then you can create an object of the class called **bicycle**.

### **Declaring Object In Dart**

Once you have created a class, it’s time to declare the object. You can declare an object by the following syntax:

### **Syntax**

```
ClassName objectName = ClassName();

```


### **Example : Declaring An Object In Dart**

In this example below, there is class **Bycycle** with three properties: **color**, **size**, and **currentSpeed**. The class has two methods. One is **changeGear**, which changes the gear of the bicycle, and **display** method prints out the values of the three properties. We also have an object of the class **Bycycle** called **bicycle**.

```
    class Bicycle {
      String? color;
      int? size;
      int? currentSpeed;
    
      void changeGear(int newValue) {
        currentSpeed = newValue;
      }
    
      void display() {
        print("Color: $color");
        print("Size: $size");
        print("Current Speed: $currentSpeed");
      }
    }

    void main(){
        // Here bicycle is object of class Bicycle. 
        Bicycle bicycle = Bicycle();
        bicycle.color = "Red";
        bicycle.size = 26;
        bicycle.currentSpeed = 0;
        bicycle.changeGear(5);
        bicycle.display();
    }

```


[Run Online](https://dartpad.dev/?id=ac6ab46115153304cc99e2054c93cc17)

Info

**Note**: Once you create an object, you can access the properties and methods of the object using the dot(.) operator.

### **Key Points**

*   The main method is the program’s entry point, so it is always needed to see the result.
*   The **new** keyword can be used to create a new object, but it is unnecessary.

## Constructor in Dart 
### **Introduction**

In this section, you will learn about constructor in Dart programming language and how to use constructors with the help of examples. Before learning about the constructor, you should have a basic understanding of the class and object in dart.

### **Constructor In Dart**

**A constructor** is a special method used to initialize an object. It is called automatically when an object is created, and it can be used to set the initial values for the object’s properties. For example, the following code creates a **Person** class object and sets the initial values for the **name** and **age** properties.

```
Person person = Person("John", 30);

```
### **Without Constructor**

If you don’t define a constructor for class, then you need to set the values of the properties manually. For example, the following code creates a **Person** class object and sets the values for the **name** and **age** properties.

```
Person person = Person();
person.name = "John";
person.age = 30;

```

### **Things To Remember**

*   The constructor’s name should be the same as the class name.
*   Constructor doesn’t have any return type.

### Syntax

```
class ClassName {
  // Constructor declaration: Same as class name
  ClassName() {
    // body of the constructor
  }
}

```
**Note**: When you create a object of a class, the constructor is called automatically. It is used to initialize the values when an object is created.

### **Example 1: How To Declare Constructor In Dart**

In this example below, there is a class **Student** with three properties: **name**, **age**, and **rollNumber**. The class has one constructor. The constructor is used to initialize the values of the three properties. We also created an object of the class **Student** called **student**.

```
class Student {
  String? name;
  int? age;
  int? rollNumber;

  // Constructor
  Student(String name, int age, int rollNumber) {
    print(
        "Constructor called"); // this is for checking the constructor is called or not.
    this.name = name;
    this.age = age;
    this.rollNumber = rollNumber;
  }
}

void main() {
  // Here student is object of class Student.
  Student student = Student("John", 20, 1);
  print("Name: ${student.name}");
  print("Age: ${student.age}");
  print("Roll Number: ${student.rollNumber}");
}

```

[Run Online](https://dartpad.dev/?id=272408e52010155b508050093eda4c91)

Info

**Note**: The **this** keyword is used to refer to the current instance of the class. It is used to access the current class properties. In the example above, parameter names and class properties of constructor **Student** are the same. Hence to avoid confusion, we use the **this** keyword.

### **Example 2: Constructor In Dart**

In this example below, there is a class **Teacher** with four properties: **name**, **age**, **subject**, and **salary**. Class has one constructor for initializing the values of the properties. Class also contain method **display()** which is used to display the values of the properties. We also created 2 objects of the class **Teacher** called **teacher1** and **teacher2**.

```
class Teacher {
  String? name;
  int? age;
  String? subject;
  double? salary;

  // Constructor
  Teacher(String name, int age, String subject, double salary) {
    this.name = name;
    this.age = age;
    this.subject = subject;
    this.salary = salary;
  }
  // Method
  void display() {
    print("Name: ${this.name}");
    print("Age: ${this.age}");
    print("Subject: ${this.subject}");
    print("Salary: ${this.salary}\n"); // \n is used for new line
  }
}

void main() {
  // Creating teacher1 object of class Teacher
  Teacher teacher1 = Teacher("John", 30, "Maths", 50000.0);
  teacher1.display();

  // Creating teacher2 object of class Teacher
  Teacher teacher2 = Teacher("Smith", 35, "Science", 60000.0);
  teacher2.display();
}

```
[Run Online](https://dartpad.dev/?id=feca294afc69f2a6e40c72e94bacff4f)

Info

**Note**: You can create many objects of a class. Each object will have its own copy of the properties.

### **Example 3: Constructor In Dart**

In this example below, there is a class **Car** with two properties: **name** and **price**. The class has one constructor for initializing the values of the properties. The class also contains method **display()**, which is used to display the values of the properties. We also created an object of the class **Car** called **car**.

```
 class Car {
  String? name;
  double? price;

  // Constructor
  Car(String name, double price) {
    this.name = name;
    this.price = price;
  }

  // Method
  void display() {
    print("Name: ${this.name}");
    print("Price: ${this.price}");
  }
}

void main() {
  // Here car is object of class Car.
  Car car = Car("BMW", 500000.0);
  car.display();
}

```

[Run Online](https://dartpad.dev/?id=df9f4ebe50ab75c11e9f70c1dd9781bb)

### **Example 4: Constructor In Dart**

In this example below, there is a class **Staff** with four properties: **name**, **phone1**, **phone2**, and **subject** and one method **display()**. Class has one constructor for initializing the values of only **name**, **phone1** and **subject**. We also created an object of the class **Staff** called **staff**.

```
 class Staff {
  String? name;
  int? phone1;
  int? phone2;
  String? subject;

  // Constructor
  Staff(String name, int phone1, String subject) {
    this.name = name;
    this.phone1 = phone1;
    this.subject = subject;
  }

  // Method
  void display() {
    print("Name: ${this.name}");
    print("Phone1: ${this.phone1}");
    print("Phone2: ${this.phone2}");
    print("Subject: ${this.subject}");
  }
}

void main() {
  // Here staff is object of class Staff.
  Staff staff = Staff("John", 1234567890, "Maths");
  staff.display();
}

```

[Run Online](https://dartpad.dev/?id=b1c03fbb1b0169c623df475cd31ce4c8)

### **Example 5: Write Constructor Single Line**

In the avobe section, you have written the constructor in long form. You can also write the constructor in short form. You can directly assign the values to the properties. For example, the following code is the short form of the constructor in one line.

```
class Person{
  String? name;
  int? age;
  String? subject;
  double? salary;

  // Constructor in short form
  Person(this.name, this.age, this.subject, this.salary);

  // display method
  void display(){
    print("Name: ${this.name}");
    print("Age: ${this.age}");
    print("Subject: ${this.subject}");
    print("Salary: ${this.salary}");
  }
}

void main(){
  Person person = Person("John", 30, "Maths", 50000.0);
  person.display();
}

```
[Run Online](https://dartpad.dev/?id=28abe898777d13770dd239aa836c83e3)

### **Example 6: Constructor With Optional Parameters**

In the example below, we have created a class **Employee** with four properties: **name**, **age**, **subject**, and **salary**. Class has one constructor for initializing the all properties values. For **subject** and **salary**, we have used optional parameters. It means we can pass or not pass the values of **subject** and **salary**. The Class also contain method **display()** which is used to display the values of the properties. We also created an object of the class **Employee** called **employee**.

```
class Employee {
  String? name;
  int? age;
  String? subject;
  double? salary;

  // Constructor
  Employee(this.name, this.age, [this.subject = "N/A", this.salary=0]);

  // Method
  void display() {
    print("Name: ${this.name}");
    print("Age: ${this.age}");
    print("Subject: ${this.subject}");
    print("Salary: ${this.salary}");
  }
}

void main(){
  Employee employee = Employee("John", 30);
  employee.display();
}

```

[Run Online](https://dartpad.dev/?id=841e4c019446527d2fddcb7a92c3fa3e)

### **Example 7: Constructor With Named Parameters**

In the example below, we have created a class **Chair** with two properties: **name** and **color**. Class has one constructor for initializing the all properties values with named parameters. The Class also contain method **display()** which is used to display the values of the properties. We also created an object of the class **Chair** called **chair**.

```
class Chair {
String? name;
String? color;

// Constructor
Chair({this.name, this.color});

// Method
void display() {
  print("Name: ${this.name}");
  print("Color: ${this.color}");
}
}

void main(){
Chair chair = Chair(name: "Chair1", color: "Red");
chair.display();
}

```

[Run Online](https://dartpad.dev/?id=9aa428d7c5e498d5233345470cf299c4)

### **Example 8: Constructor With Default Values**

In the example below, we have created a class **Table** with two properties: **name** and **color**. Class has one constructor for initializing the all properties values with default values. The Class also contain method **display()** which is used to display the values of the properties. We also created an object of the class **Table** called **table**.

```
class Table {
  String? name;
  String? color;

  // Constructor
  Table({this.name = "Table1", this.color = "White"});

  // Method
  void display() {
    print("Name: ${this.name}");
    print("Color: ${this.color}");
  }
}

void main(){
  Table table = Table();
  table.display();
}

```

[Run Online](https://dartpad.dev/?id=a6e04e8b75208952220b899e13e60feb)

### **Key Points**

*   The constructor’s name should be the same as the class name.
*   Constructor doesn’t have any return type.
*   Constructor is only called once at the time of the object creation.
*   Constructor is called automatically when an object is created.
*   Constructor is used to initialize the values of the properties of the class.

