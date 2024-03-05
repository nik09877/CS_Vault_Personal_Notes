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

