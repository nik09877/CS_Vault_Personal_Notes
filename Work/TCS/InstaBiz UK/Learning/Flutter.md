# Introduction
- use `ctrl + space` to check all the parameters of a Widget.
- Widgets describe what the view should look like given the current configuration and state
- Material is a conceptual piece of paper on which the UI appears.
- Flutter provides a number of widgets that help you build apps that follow Material Design. A Material app starts with the [`MaterialApp`](https://api.flutter.dev/flutter/material/MaterialApp-class.html) widget, which builds a number of useful widgets at the root of your app, including a [`Navigator`](https://api.flutter.dev/flutter/widgets/Navigator-class.html), which manages a stack of widgets identified by strings, also known as “routes”. The `Navigator` lets you transition smoothly between screens of your application.
- Scaffold is a layout for the major Material Components.
- The BuildContext indicates where the build is taking place
- Keys are most useful in widgets that build many instances of the same type of widget.
- Use global keys to uniquely identify child widgets. Global keys must be globally unique across the entire widget hierarchy, unlike local keys which need only be unique among siblings. Because they are globally unique, a global key can be used to retrieve the state associated with a widget.
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
  State<MyStatefulWidget> createState() => _MyStatefulWidgetState();
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

You might wonder why `StatefulWidget` and `State` are separate objects. In Flutter, these two types of objects have different life cycles. `Widgets` are temporary objects, used to construct a presentation of the application in its current state. `State` objects, on the other hand, are persistent between calls to `build()`, allowing them to remember information.

```dart
import 'package:flutter/material.dart';

class CounterDisplay extends StatelessWidget {
  const CounterDisplay({required this.count, super.key});

  final int count;

  @override
  Widget build(BuildContext context) {
    return Text('Count: $count');
  }
}

class CounterIncrementor extends StatelessWidget {
  const CounterIncrementor({required this.onPressed, super.key});

  final VoidCallback onPressed;

  @override
  Widget build(BuildContext context) {
    return ElevatedButton(
      onPressed: onPressed,
      child: const Text('Increment'),
    );
  }
}

class Counter extends StatefulWidget {
  const Counter({super.key});

  @override
  State<Counter> createState() => _CounterState();
}

class _CounterState extends State<Counter> {
  int _counter = 0;

  void _increment() {
    setState(() {
      ++_counter;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Row(
      mainAxisAlignment: MainAxisAlignment.center,
      children: <Widget>[
        CounterIncrementor(onPressed: _increment),
        const SizedBox(width: 16),
        CounterDisplay(count: _counter),
      ],
    );
  }
}

void main() {
  runApp(
    const MaterialApp(
      home: Scaffold(
        body: Center(
          child: Counter(),
        ),
      ),
    ),
  );
}
```

#### Complicated
```dart
import 'package:flutter/material.dart';

class Product {
  const Product({required this.name});

  final String name;
}

typedef CartChangedCallback = Function(Product product, bool inCart);

class ShoppingListItem extends StatelessWidget {
  ShoppingListItem({
    required this.product,
    required this.inCart,
    required this.onCartChanged,
  }) : super(key: ObjectKey(product));

  final Product product;
  final bool inCart;
  final CartChangedCallback onCartChanged;

  Color _getColor(BuildContext context) {
    // The theme depends on the BuildContext because different
    // parts of the tree can have different themes.
    // The BuildContext indicates where the build is
    // taking place and therefore which theme to use.

    return inCart //
        ? Colors.black54
        : Theme.of(context).primaryColor;
  }

  TextStyle? _getTextStyle(BuildContext context) {
    if (!inCart) return null;

    return const TextStyle(
      color: Colors.black54,
      decoration: TextDecoration.lineThrough,
    );
  }

  @override
  Widget build(BuildContext context) {
    return ListTile(
      onTap: () {
        onCartChanged(product, inCart);
      },
      leading: CircleAvatar(
        backgroundColor: _getColor(context),
        child: Text(product.name[0]),
      ),
      title: Text(
        product.name,
        style: _getTextStyle(context),
      ),
    );
  }
}

class ShoppingList extends StatefulWidget {
  const ShoppingList({required this.products, super.key});

  final List<Product> products;

  // The framework calls createState the first time
  // a widget appears at a given location in the tree.
  // If the parent rebuilds and uses the same type of
  // widget (with the same key), the framework re-uses
  // the State object instead of creating a new State object.

  @override
  State<ShoppingList> createState() => _ShoppingListState();
}

class _ShoppingListState extends State<ShoppingList> {
  final _shoppingCart = <Product>{};

  void _handleCartChanged(Product product, bool inCart) {
    setState(() {
      // When a user changes what's in the cart, you need
      // to change _shoppingCart inside a setState call to
      // trigger a rebuild.
      // The framework then calls build, below,
      // which updates the visual appearance of the app.

      if (!inCart) {
        _shoppingCart.add(product);
      } else {
        _shoppingCart.remove(product);
      }
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Shopping List'),
      ),
      body: ListView(
        padding: const EdgeInsets.symmetric(vertical: 8),
        children: widget.products.map((product) {
          return ShoppingListItem(
            product: product,
            inCart: _shoppingCart.contains(product),
            onCartChanged: _handleCartChanged,
          );
        }).toList(),
      ),
    );
  }
}

void main() {
  runApp(const MaterialApp(
    title: 'Shopping App',
    home: ShoppingList(
      products: [
        Product(name: 'Eggs'),
        Product(name: 'Flour'),
        Product(name: 'Chocolate chips'),
      ],
    ),
  ));
}
```
### Key Points:

- Stateless widgets are immutable and don't have mutable state.
- Stateful widgets have mutable state and can be updated over time.
- Stateful widgets have a corresponding state class that extends `State`.
- `setState` is used to notify Flutter to rebuild the widget when the state changes.

Understanding the distinction between stateful and stateless widgets is fundamental when working with Flutter, as it influences how you design and structure your UI components.

# Widgets

### 1. `Container`:

A `Container` is a box model that can contain other widgets.

```dart
Container(
  color: Colors.blue,
  width: 200,
  height: 100,
  child: Text('Hello, Container!'),
)
```

### 2. `Row`:

A `Row` widget arranges its children in a horizontal line.

```dart
Row(
  children: [
    Text('Hello,'),
    Text(' Flutter!'),
  ],
)
```

### 3. `Column`:

A `Column` widget arranges its children in a vertical line.

```dart
Column(
  children: [
    Text('Hello,'),
    Text(' Flutter!'),
  ],
)
```

### 4. `ListView`:

A `ListView` is a scrollable list of widgets.

```dart
ListView(
  children: [
    ListTile(title: Text('Item 1')),
    ListTile(title: Text('Item 2')),
    ListTile(title: Text('Item 3')),
  ],
)
```

### 5. `GridView`:

A `GridView` is a scrollable grid of widgets.

```dart
GridView.builder(
  gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
    crossAxisCount: 2,
  ),
  itemBuilder: (context, index) => ListTile(title: Text('Item $index')),
)
```

### 6. `Stack` and `Positioned`:

A `Stack` allows widgets to be overlaid on top of each other. `Positioned` widgets control the positioning of children within the `Stack`.

```dart
Stack(
  children: [
    Positioned(
      left: 10,
      top: 10,
      child: Text('Positioned 1'),
    ),
    Positioned(
      right: 10,
      bottom: 10,
      child: Text('Positioned 2'),
    ),
  ],
)
```

### 7. `AppBar`:

An `AppBar` is a material design app bar that typically contains the title and optional actions.

```dart
AppBar(
  title: Text('My App'),
  actions: [
    IconButton(
      icon: Icon(Icons.settings),
      onPressed: () {
        // Handle settings button press
      },
    ),
  ],
)
```

### 8. `Scaffold`:

A `Scaffold` is a top-level container that holds the structure of the visual interface.

```dart
Scaffold(
  appBar: AppBar(
    title: Text('My App'),
  ),
  body: Center(
    child: Text('Hello, Flutter!'),
  ),
)
```

### 9. `Text`:

A `Text` widget displays a paragraph of text.

```dart
Text('Hello, Flutter!')
```

### 10. `Image`:

An `Image` widget displays an image from a specified asset, network, or file.

```dart
Image.network('https://example.com/image.jpg')
```

### 11. `Icon`:

An `Icon` widget displays a graphic symbol representing a command.

```dart
Icon(Icons.star)
```

### 12. Different Types of Buttons:

Flutter provides various button widgets, including `ElevatedButton`, `TextButton`, and `OutlinedButton`.

```dart
ElevatedButton(onPressed: () {}, child: Text('Elevated Button'))
TextButton(onPressed: () {}, child: Text('Text Button'))
OutlinedButton(onPressed: () {}, child: Text('Outlined Button'))
IconButton(onPresses:(){},icon:Icon(Icons.cart))
```

### 13. `TextField`:

A `TextField` widget allows the user to enter text.

```dart
TextField(
  decoration: InputDecoration(labelText: 'Username'),
)
```

### 14. `Form`:

  
Forms are essential elements for collecting user input in Flutter applications. Here's an overview of building forms in Flutter:

**Creating a Form:**

- The `Form` widget acts as a container for your form fields.
- Use a `GlobalKey` to uniquely identify the form and enable validation later.


```dart
final _formKey = GlobalKey<FormState>();

Form(
  key: _formKey,
  // ...your form fields here
)
```


**Adding Form Fields:**

- Wrap each input field with a `FormField` widget to manage its state and validation.
- Use different field types like `TextFormField` for text input, `Checkbox` for boolean choices, etc.


```dart
TextFormField(
  validator: (value) => value!.isEmpty ? 'Field cannot be empty' : null,
  decoration: InputDecoration(
    labelText: 'Name',
  ),
),

Checkbox(
  value: _isChecked,
  onChanged: (bool? value) {
    setState(() {
      _isChecked = value!;
    });
  },
),
```

**Validation:**

- You can define validation logic for each field using the `validator` property of the `FormField`.
- Use the `Form.validate()` method to check if all fields are valid before submitting the form.


```dart
if (_formKey.currentState!.validate()) {
  // Submit the form
}
```


**Submitting the Form:**

- Use a button or similar widget to trigger form submission.
- In the button's onPressed handler, access the form state using `_formKey.currentState` and handle form data.

```dart
ElevatedButton(
  onPressed: () {
    if (_formKey.currentState!.validate()) {
      // Get data from form fields
      final name = _formKey.currentState!.fields['name']!.value!;
      // Process or send data
    }
  },
  child: Text('Submit'),
),
```

**Additional Tips:**

- Handle focus and errors for a better user experience.
- Consider pre-filling fields with existing data.
- Explore packages like `form_validator` or `bloc_form` for advanced validation and form management.

Remember, this is a basic overview. Flutter's built-in widgets and packages offer extensive options to customize and enhance your forms.

### 15. `Card`:

A `Card` widget is a material design card.

```dart
Card(
  child: ListTile(
    title: Text('Card Title'),
    subtitle: Text('Card Subtitle'),
    leading: Icon(Icons.star),
    trailing: IconButton(
      icon: Icon(Icons.favorite),
      onPressed: () {
        // Handle favorite button press
      },
    ),
  ),
)
```

### 16. `AlertDialog`:

An `AlertDialog` displays an alert dialog to the user.

```dart
ElevatedButton(
  onPressed: () {
    showDialog(
      context: context,
      builder

: (BuildContext context) {
        return AlertDialog(
          title: Text('Alert Dialog'),
          content: Text('This is an alert message.'),
          actions: [
            TextButton(
              onPressed: () {
                Navigator.of(context).pop(); // Close the dialog
              },
              child: Text('OK'),
            ),
          ],
        );
      },
    );
  },
  child: Text('Show Alert'),
)
```

### 17. `BottomSheet`:

A `BottomSheet` displays a sheet from the bottom of the screen.

```dart
ElevatedButton(
  onPressed: () {
    showModalBottomSheet(
      context: context,
      builder: (BuildContext context) {
        return Container(
          height: 200,
          child: Center(
            child: Text('Bottom Sheet Content'),
          ),
        );
      },
    );
  },
  child: Text('Show Bottom Sheet'),
)
```

### 18. `Drawer`:

A `Drawer` widget creates a material design drawer.

```dart
Scaffold(
  appBar: AppBar(
    title: Text('My App'),
  ),
  drawer: Drawer(
    child: ListView(
      padding: EdgeInsets.zero,
      children: [
        DrawerHeader(
          child: Text('Drawer Header'),
          decoration: BoxDecoration(
            color: Colors.blue,
          ),
        ),
        ListTile(
          title: Text('Item 1'),
          onTap: () {
            // Handle item 1 tap
          },
        ),
        ListTile(
          title: Text('Item 2'),
          onTap: () {
            // Handle item 2 tap
          },
        ),
      ],
    ),
  ),
  body: Center(
    child: Text('Hello, Flutter!'),
  ),
)
```

### 19. `TabBar` and `TabView`:

A `TabBar` displays a horizontal row of tabs, and `TabView` displays the corresponding tab views.

```dart
DefaultTabController(
  length: 2,
  child: Scaffold(
    appBar: AppBar(
      title: Text('Tabs Example'),
      bottom: TabBar(
        tabs: [
          Tab(icon: Icon(Icons.tab)),
          Tab(icon: Icon(Icons.tab)),
        ],
      ),
    ),
    body: TabBarView(
      children: [
        Center(child: Text('Tab 1')),
        Center(child: Text('Tab 2')),
      ],
    ),
  ),
)
```

### 20. `Expanded` and `Flexible`:

`Expanded` and `Flexible` are used to control how a widget flexes within a `Column` or `Row`.

```dart
Column(
  children: [
    Expanded(
      child: Container(color: Colors.red),
    ),
    Expanded(
      child: Container(color: Colors.blue),
    ),
  ],
)
```

### 21. `GestureDetector`:

A `GestureDetector` allows you to capture gestures such as taps and swipes.

```dart
GestureDetector(
  onTap: () {
    // Handle tap
  },
  child: Container(
    color: Colors.green,
    child: Center(child: Text('Tap me!')),
  ),
)
```

### 22. `FutureBuilder`:

A `FutureBuilder` is used to build a widget tree based on the latest snapshot of an asynchronous computation.

```dart
Future fetchData()async{
	//fetch all data 
}
@override
Widget build(BuildContext context){
	return FutureBuilder<String>(
	  future: fetchData(), // async function that produces a future
	  builder: (context, snapshot) {
		if (snapshot.connectionState == ConnectionState.waiting) {
		  return CircularProgressIndicator();
		} else if (snapshot.hasError) {
		  return Text('Error: ${snapshot.error}');
		} else {
		  return Text('Data: ${snapshot.data}');
		}
	  },
	)
}

```

### 23. `StreamBuilder`:
A **Stream** is a collection of **Futures**.

A `StreamBuilder` is similar to `FutureBuilder` but for asynchronous streams.

```dart
StreamBuilder<int>(
  stream: countStream(),
  builder: (context, snapshot) {
    if (snapshot.connectionState == ConnectionState.waiting) {
      return CircularProgressIndicator();
    } else if (snapshot.hasError) {
      return Text('Error: ${snapshot.error}');
    } else {
      return Text('Count: ${snapshot.data}');
    }
  },
)
```

### 24. `InkWell`:
- **Purpose:** Adds a splash effect and click functionality to any widget wrapped within it. This is used for creating interactive elements like buttons and links.
- **Properties:** You can customize the splash color, highlight color, shape, and tap callback function.
```dart
InkWell(
  onTap: () {
    print("Tapped!");
  },
  child: Text("Click Me"),
),

```

### 25. `Chip`:
- **Purpose:** Represents a small, self-contained piece of information with a close button. Used for things like tags, filters, or recently selected items.
- **Properties:** You can customize the text, avatar, shape, color, deletion icon, and tap callback function.
```dart
Chip(
  label: Text("Flutter"),
  avatar: Icon(Icons.flutter),
  onDeleted: () {
    // Handle deletion here
  },
),
```
### `SingleChildScrollView`:
- `SingleChildScrollView + Column = ListView`
- The `SingleChildScrollView` widget in Flutter is a versatile tool for making any single child widget scrollable. It's useful when:

**1. Limited Screen Space:**

- Your content exceeds the available screen size in one direction (vertically or horizontally).
- You want to ensure users can access all content by scrolling.

**2. Shrink-wrapping:**

- You want the scrollable area to adjust its size based on its content's size.
- This is common in dialogs, pop-up menus, or flexible layouts.

**3. Controlled Scrolling:**

- You need to control the scroll behavior (e.g., enabling/disabling, snapping to positions).
- Use its properties like `scrollDirection`, `reverse`, and `controller` for customization.

**Key Properties:**

- **child:** The single widget you want to make scrollable.
- **scrollDirection:** Specifies the scrolling direction (horizontal or vertical).
- **reverse:** If true, scrolling is reversed (opposite direction).
- **padding:** Adds padding around the content within the scroll view.
- **physics:** Defines the scroll behavior (e.g., bouncing, no resistance).
- **controller:** Allows controlling the scroll position programmatically.

**Common Use Cases:**

- Lists of items that overflow the screen height.
- Long text content needing vertical scrolling.
- Image viewers or carousels requiring horizontal scrolling.
- Complex layouts with dynamic content needing adaptable scrolling.

**Remember:**

- While `SingleChildScrollView` is easy to use, consider `ListView` for longer lists with efficient rendering.
- Be mindful of accessibility when implementing scrolling content.
- Nested scrollable widgets require careful configuration to avoid conflicts.
```dart
SingleChildScrollView(
  child: Column(
    children: [
      Text("Scrollable content 1"),
      Text("Scrollable content 2"),
      Text("Scrollable content 3"),
    ],
  ),
);

```
# Responsive Layouts in Flutter: Essential Widgets and Code Examples

### **MediaQuery:**
    
    - Provides device specifics like size, orientation, etc.
    - Example:

```dart
MediaQueryData mediaQuery = MediaQuery.of(context);
double screenWidth = mediaQuery.size.width;

if (screenWidth > 600) {
  // Use a wider layout for larger screens
} else {
  // Use a narrower layout for smaller screens
}
```

### **LayoutBuilder:**
    
    - Rebuilds when layout constraints change, providing access to those constraints.

```dart
LayoutBuilder(
  builder: (context, constraints) {
    if (constraints.maxWidth > 600) {
      // Use a wider layout for larger screens
    } else {
      // Use a narrower layout for smaller screens
    }
  },
);
```

### **Row:** 
Arranges children horizontally.

```dart
Row(
  children: [
    Expanded(child: Text("Left content")),
    Expanded(child: Text("Right content")),
  ],
);
```

Use code with caution. [Learn more](https://gemini.google.com/faq#coding)

content_copy

### **Column:** 
Arranges children vertically.

```dart
Column(
  children: [
    Text("Top content"),
    Text("Middle content"),
    Text("Bottom content"),
  ],
);
```

### **Wrap:** 
Arranges children in a wrap-around fashion.

```dart
Wrap(
  children: [
    Text("Text 1"),
    Text("Text 2"),
    Text("Text 3"),
  ],
);
```

### **AspectRatio:** 
Maintains a specific aspect ratio for its child.

```dart
AspectRatio(
  aspectRatio: 16 / 9,
  child: Image.network("your_image_url"),
);
```

### **Flexible:** 
Allows child to flex within a row or column based on a flex factor.

```dart
Row(
  children: [
    Flexible(flex: 2, child: Text("Wider section")),
    Flexible(flex: 1, child: Text("Narrower section")),
  ],
);
```
### **Expanded:**
- Use `Expanded` when you want the child to fill any remaining space in its parent, regardless of its preferred size.
- |Feature|Flexible|Expanded|
|---|---|---|
|Purpose|Flexible size based on factor|Fill remaining space|
|Respects child size|Yes|No|
|Fills remaining space|Proportionally|Equally (with other Expanded|
```dart
Row(
  children: [
    Text("Fixed text"),
    Expanded(child: ElevatedButton(onPressed: () {}, child: Text("Fill rest"))),
  ],
);

```
**Flexible:**

- **Purpose:** Allows its child to flex within a row or column based on a **flex factor**.
- **Behavior:**
    
    - Respects its child's preferred size if possible.
    - Takes up remaining space in its parent **proportionally** to its flex factor compared to other `Flexible` widgets within the same row/column.
    - Does not force its child to fit its own size.
    

**Expanded:**

- **Purpose:** Forces its child to **fill the remaining available space** in its parent.
- **Behavior:**
    - Ignores the preferred size of its child.
    - Expands its child to fill the remaining space, potentially causing resizing or overflow if the child has fixed dimensions.
    - If multiple `Expanded` widgets are used in the same row/column, they share the remaining space **equally**.
### **FractionallySizedBox:** 
Allocates a specific fraction of its parent's size to its child.
```dart
FractionallySizedBox(
  widthFactor: 0.5,
  child: Text("Half width content"),
);
```

**IV. Additional Techniques:**

- **Media Queries:** Define different styles or layouts for specific screen sizes/orientations.
- **Breakpoints:** Set specific points where layout changes significantly for different device groups.
- **State Management:** Use solutions like Provider or BLoC to share layout information and adapt UI dynamically.

**Remember:** Test your app on various devices and orientations for a seamless user experience.

**Note:** This is a basic overview. Explore documentation and resources for more advanced techniques and widget options.
# GetX 
GetX is a Flutter package that provides a lightweight and powerful state management solution. It is designed to be simple, yet highly efficient, and it offers various features for managing both local and global states in Flutter applications. Here's an overview of key concepts and features of GetX state management:

### Key Concepts:

1. **Reactive State Management:**
   - GetX utilizes a reactive programming paradigm. Widgets can subscribe to changes in a specific piece of state, and they automatically rebuild when that state changes.

2. **Controllers:**
   - In GetX, controllers are used to manage state. A controller is a class that extends `GetxController`. It holds the state and business logic for a particular feature or screen.

3. **Observables:**
   - Variables in a GetX controller can be marked as observables using the `Rx` class. These observables notify subscribers when their values change.

4. **Reactive Widgets:**
   - GetX provides reactive widget extensions that allow you to easily listen to changes in observables and trigger widget rebuilds. For example, `Obx(() => YourWidget())` automatically rebuilds when an observable changes.

5. **Dependency Injection:**
   - GetX includes a lightweight dependency injection system. Controllers and other dependencies can be injected into widgets using `Get.put` or `Get.find`.

6. **Named Routes:**
   - GetX simplifies navigation with named routes. You can define routes using `GetPage` and navigate to them using `Get.toNamed` or `Get.offNamed`.

### Example:

Let's create a simple example to demonstrate the basic usage of GetX:

```dart
import 'package:flutter/material.dart';
import 'package:get/get.dart';

class CounterController extends GetxController {
  var counter = 0.obs;
  void increment() => counter++;
}

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return GetMaterialApp(
      title: 'GetX Example',
      home: HomePage(),
    );
  }
}

class HomePage extends StatelessWidget {
  final CounterController controller = Get.put(CounterController());

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('GetX Counter Example'),
      ),
      body: Center(
        child: Obx(
          () => Text(
            'Counter Value: ${controller.counter.value}',
            style: TextStyle(fontSize: 24),
          ),
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: () => controller.increment(),
        child: Icon(Icons.add),
      ),
    );
  }
}
```

In this example:

- `CounterController` manages the state (counter) and provides the `increment` method to modify the state.
- The `Obx` widget listens to changes in the `counter` observable and automatically rebuilds the UI when it changes.
- The `Get.put` method injects the controller into the widget tree.

### Benefits of GetX:

- **Simplicity:** GetX is known for its simplicity and ease of use.
- **Performance:** It is designed to be highly performant with minimal boilerplate code.
- **Reactivity:** Widgets automatically rebuild when the observed state changes.
- **Lightweight:** GetX has a small footprint and doesn't rely on code generation.

GetX is suitable for a wide range of Flutter applications, from small projects to larger, more complex ones. It's particularly popular for its ease of use and effectiveness in managing state in a reactive manner.


# Clean Architecture
![Clean Arch](Pasted_image_20240211133118.png)
- `blurRadius` should be 2 or 1.5 times the `offset`.
```dart
BoxShadow(
  offset: Offset(0, 2),
  blurRadius: 4,
  color: Colors.black12),
```

- What to do for text overflow?
```dart
Text("News title",
  maxLines: 2,
  style: TextStyle(
	  overflow: TextOverflow.ellipsis,
  ))
```
- If you want a `ListView` inside a `Column`, wrap it in an `Expanded` Widget