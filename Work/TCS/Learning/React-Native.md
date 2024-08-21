# Day 1
### What is React Native?
React Native is an open-source framework developed by Facebook for building mobile applications using JavaScript and React. It allows developers to use the same codebase to create native-like mobile applications for both iOS and Android platforms. React Native is built on top of the React library, which is a JavaScript library for building user interfaces.

Key features of React Native include:

1. **Cross-Platform Development:** With React Native, developers can write code once and run it on both iOS and Android platforms, reducing development time and effort.

2. **Reusable Components:** React Native enables the creation of reusable components, allowing developers to build modular and maintainable code.

3. **Hot Reloading:** This feature allows developers to see the results of their code changes in real-time without rebuilding the entire application, which speeds up the development process.

4. **Native Performance:** React Native applications are not web apps wrapped in a native shell; instead, they use native components, resulting in performance comparable to applications developed using native languages like Swift for iOS or Java/Kotlin for Android.

5. **Large Community and Ecosystem:** React Native has a large and active community of developers, which means extensive documentation, third-party libraries, and community support.

6. **React Integration:** React Native leverages the concepts of React, such as the virtual DOM and declarative programming, making it easier for developers familiar with React to transition to mobile app development.

While React Native has gained popularity for its cross-platform capabilities and development speed, it may not be the best choice for every mobile app project. Factors such as app complexity, performance requirements, and the need for platform-specific features should be considered when choosing a mobile development framework.
### Use of React Native
React Native is widely used for developing mobile applications, and its popularity stems from several advantages it offers. Here are some common use cases for React Native:

1. **Cross-Platform Mobile Apps:** React Native is ideal for projects that require a single codebase to deploy on both iOS and Android platforms. This significantly reduces development time and effort compared to building separate native apps for each platform.

2. **Development Speed:** React Native's hot-reloading feature allows developers to see the results of code changes in real-time, speeding up the development process. This is particularly beneficial for rapid prototyping and iterative development.

3. **Code Reusability:** React Native allows for a high degree of code reusability. Developers can reuse components across different parts of the application or even in different projects, making it easier to maintain and update code.

4. **Cost-Effective Development:** Since React Native enables cross-platform development, businesses can save on development costs by maintaining a single codebase for both iOS and Android applications. This is especially advantageous for startups and small to medium-sized enterprises.

5. **Web Developers Transitioning to Mobile:** Developers familiar with web technologies, particularly those who have worked with React, can leverage their existing skills to build mobile applications using React Native. This facilitates a smoother transition for web developers entering the mobile app development space.

6. **Enterprise Applications:** React Native is suitable for building enterprise-level mobile applications where rapid development, cost efficiency, and cross-platform compatibility are key considerations.

7. **Prototyping and MVPs:** React Native is well-suited for building prototypes and Minimum Viable Products (MVPs). Its quick development cycle allows businesses to test their app ideas and gather user feedback before investing in more extensive development.

8. **Community and Ecosystem:** The large and active React Native community provides a wealth of resources, libraries, and plugins. This makes it easier for developers to find solutions to common problems and accelerates the development process.

9. **Updates and Maintenance:** With a single codebase, updates and maintenance become more straightforward. Changes made to the codebase are reflected on both iOS and Android platforms simultaneously, reducing the effort required for keeping the app up-to-date.

While React Native is a versatile framework, it's essential to consider the specific requirements of your project, including performance needs, access to native APIs, and the potential need for platform-specific features. In some cases, native development might be more appropriate, but React Native remains a powerful choice for a wide range of mobile app projects.
### Alternatives of React Native
Several alternatives to React Native exist, each with its own strengths, weaknesses, and use cases. Here are some popular alternatives:

1. **Flutter:**
   - **Developed by:** Google
   - **Language:** Dart
   - **Key Features:** Uses a compiled language (Dart) and a customizable UI toolkit, providing a consistent look and feel across platforms. Hot reload functionality is also available.

2. **NativeScript:**
   - **Developed by:** Progress
   - **Languages:** JavaScript, TypeScript
   - **Key Features:** Allows developers to build native apps using JavaScript or TypeScript. Supports Angular and Vue.js for building UI components.

3. **Xamarin:**
   - **Developed by:** Microsoft
   - **Language:** C#
   - **Key Features:** Allows developers to use C# for cross-platform development, sharing a significant portion of the codebase. Provides access to native APIs and integrates well with Visual Studio.

4. **PhoneGap / Apache Cordova:**
   - **Developed by:** Adobe / Apache Software Foundation
   - **Languages:** HTML, CSS, JavaScript
   - **Key Features:** Uses web technologies to build cross-platform mobile apps. Allows for rapid development but may have some performance trade-offs compared to fully native apps.

5. **Vue Native:**
   - **Developed by:** GeekyAnts
   - **Language:** JavaScript (Vue.js)
   - **Key Features:** Integrates Vue.js with the NativeScript framework, allowing developers familiar with Vue.js to build cross-platform mobile apps.

6. **SwiftUI / UIKit (for iOS) and Jetpack Compose / Android SDK (for Android):**
   - **Developed by:** Apple (SwiftUI), Google (Jetpack Compose)
   - **Languages:** Swift (SwiftUI), Kotlin (Jetpack Compose)
   - **Key Features:** For platform-specific development, SwiftUI is used for iOS apps, and Jetpack Compose is used for Android apps. These provide a fully native experience but require separate codebases for iOS and Android.

7. **Electron:**
   - **Developed by:** GitHub (acquired by Microsoft)
   - **Languages:** HTML, CSS, JavaScript
   - **Key Features:** While primarily used for desktop applications, Electron can be considered for cross-platform development by packaging web applications into native desktop apps.

The choice between these alternatives depends on factors such as development team expertise, project requirements, performance considerations, and the need for platform-specific features. Each framework has its own set of advantages and trade-offs, so it's important to evaluate them based on the specific needs of your project.

### Environment Set up
Setting up the development environment for React Native involves several steps. Below are the general steps for setting up a React Native development environment on your machine. Keep in mind that the specific steps might vary depending on your operating system (Windows, macOS, or Linux).

#### Prerequisites:

1. **Node.js and npm:**
   - Install Node.js and npm by downloading the installer from the official website: [Node.js](https://nodejs.org/)

2. **Java Development Kit (JDK):**
   - React Native requires Java for Android development. Install JDK 8 or later. You can download it from the [Oracle website](https://www.oracle.com/java/technologies/javase-downloads.html) or use OpenJDK.

3. **Android Studio (for Android development):**
   - Download and install Android Studio from the [official website](https://developer.android.com/studio). Follow the installation instructions and make sure to install the required Android SDK components.

4. **Xcode (for iOS development - macOS only):**
   - Install Xcode from the Mac App Store if you're using macOS. It includes the necessary tools for iOS development.

#### React Native CLI Installation:
Open your terminal (or command prompt) and run the following commands:

```bash
# Install React Native CLI globally
npm install -g react-native-cli
```

#### Create a new React Native project:

```bash
# Create a new React Native project
npx react-native init YourProjectName
```

#### Navigate to the project folder:

```bash
cd YourProjectName
```

#### Run the React Native application:

#### For Android:

```bash
npx react-native run-android
```

#### For iOS:

```bash
npx react-native run-ios
```

#### Additional Setup (Optional):

1. **Watchman (Optional):**
   - Watchman can improve the performance of the development server. Install it using your system's package manager (e.g., Homebrew on macOS).

   ```bash
   brew install watchman
   ```

2. **Editor Configuration (Optional):**
   - Set up an editor or integrated development environment (IDE) with React Native support. Popular choices include Visual Studio Code, Atom, and WebStorm.

#### Testing the Setup:
After running the appropriate run command (`run-android` or `run-ios`), you should see the React Native app running on an emulator or connected device.

Keep in mind that these are general steps, and there might be additional considerations based on your specific development environment. Always refer to the official React Native documentation for the most up-to-date and platform-specific instructions: [React Native - Getting Started](https://reactnative.dev/docs/environment-setup).

# Day 2

## Functional Components

In React Native, functional components are a type of component that is defined as a JavaScript function. They are also known as stateless or presentational components. Functional components have been enhanced with the introduction of React Hooks, allowing them to manage state and side effects. Below is an example of a basic functional component in React Native:

```javascript
import React from 'react';
import { View, Text } from 'react-native';

const MyFunctionalComponent = () => {
  return (
    <View>
      <Text>Hello, I am a functional component!</Text>
    </View>
  );
};

export default MyFunctionalComponent;
```

With the introduction of React Hooks, functional components can also manage state and lifecycle methods. Here's an example using the `useState` hook:

```javascript
import React, { useState } from 'react';
import { View, Text, Button } from 'react-native';

const CounterComponent = () => {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1);
  };

  return (
    <View>
      <Text>Count: {count}</Text>
      <Button title="Increment" onPress={increment} />
    </View>
  );
};

export default CounterComponent;
```

In the example above, the `useState` hook is used to declare a state variable (`count`) and a function (`setCount`) to update that state. The component renders the current count and a button that, when pressed, increments the count.

Functional components are a more concise and modern way to define components in React and React Native. They are widely used, especially for components that don't need to manage complex state or lifecycle methods.

## Class Components

In React Native, class components are a traditional way to define components using ES6 class syntax. They are also known as stateful components and are used to manage component state and lifecycle methods. Here's an example of a class component in React Native:

```javascript
import React, { Component } from 'react';
import { View, Text, Button } from 'react-native';

class CounterComponent extends Component {
  constructor(props) {
    super(props);

    this.state = {
      count: 0,
    };
  }

  increment = () => {
    this.setState({ count: this.state.count + 1 });
  };

  render() {
    return (
      <View>
        <Text>Count: {this.state.count}</Text>
        <Button title="Increment" onPress={this.increment} />
      </View>
    );
  }
}

export default CounterComponent;
```

In this example, `CounterComponent` is a class component that manages a state variable `count` and has a method `increment` to update that state. The `render` method is where the component's UI is defined.

Class components are still valid and widely used, especially when you need to manage complex state or work with lifecycle methods. However, with the introduction of React Hooks in functional components, many developers prefer functional components and hooks due to their conciseness and ease of use.

It's worth noting that with the release of React 16.8 and the introduction of Hooks, functional components have become more powerful and can handle state and lifecycle methods similarly to class components. This allows developers to choose between class components and functional components based on their preferences and project requirements.

## State

It refers to an object that represents the dynamic data that a component can maintain and manage. The state of a component can change over time in response to user interactions, network requests, or other factors. When the state of a component changes, React automatically re-renders the component to reflect the updated state.

In class components, state is typically initialized and managed using the `setState` method, while functional components use the `useState` hook for state management.

## Life Cycle Methods

In React, class components have lifecycle methods that allow developers to execute code at specific points in the component's lifecycle. React Native, being built on React, also supports these lifecycle methods. However, it's important to note that with the introduction of React Hooks in functional components, the need for class components and lifecycle methods has decreased. Hooks, such as `useEffect`, have become the preferred way to handle side effects and lifecycle events in functional components.

Here are some commonly used lifecycle methods in class components:

1. **Mounting Phase:**
   - `constructor()`: This is the constructor method called when an instance of the component is being created. It is used for initializing state and binding event handlers.
   - `componentWillMount()`: This method is called just before the component is about to mount/render.

2. **Updating Phase:**
   - `componentWillReceiveProps(nextProps)`: Invoked when the component is about to receive new props. It's deprecated, and `getDerivedStateFromProps` is recommended for derived state updates based on props.
   - `shouldComponentUpdate(nextProps, nextState)`: Returns a Boolean to determine if the component should re-render or not. It's used for performance optimization.
   - `componentWillUpdate(nextProps, nextState)`: Invoked just before rendering when new props or state are being received.
   - `render()`: The main rendering method.
   - `componentDidUpdate(prevProps, prevState)`: Called after the component updates (re-render).

3. **Unmounting Phase:**
   - `componentWillUnmount()`: Invoked immediately before a component is unmounted and destroyed. It is used for cleanup and releasing resources.

4. **Error Handling:**
   - `componentDidCatch(error, info)`: Introduced in React 16, it is used to catch JavaScript errors anywhere in the component tree and log those errors.

Here's an example demonstrating some of these lifecycle methods:

```jsx
import React, { Component } from 'react';
import { View, Text } from 'react-native';

class LifecycleExample extends Component {
  constructor(props) {
    super(props);
    this.state = {
      message: 'Hello, React Native!',
    };
    console.log('Constructor called');
  }

  static getDerivedStateFromProps(nextProps, prevState) {
    console.log('getDerivedStateFromProps called');
    // Return an object to update state based on props
    return null;
  }

  componentDidMount() {
    console.log('componentDidMount called');
  }

  componentDidUpdate(prevProps, prevState) {
    console.log('componentDidUpdate called');
  }

  componentWillUnmount() {
    console.log('componentWillUnmount called');
  }

  render() {
    console.log('render called');
    return (
      <View>
        <Text>{this.state.message}</Text>
      </View>
    );
  }
}

export default LifecycleExample;
```

Keep in mind that if you are using functional components, you'll typically use the `useEffect` hook for handling side effects and lifecycle events.

## Hooks

Hooks are a feature introduced in React 16.8 to allow functional components to have state and lifecycle features that were previously only available in class components. They provide a more direct way to use React features in functional components, making the code more concise and easier to understand.

Here are some commonly used React Hooks:

1. **useState:**
   - `useState` is used to add state to functional components.
   ```jsx
   import React, { useState } from 'react';

   function Example() {
     const [count, setCount] = useState(0);

     return (
       <div>
         <p>You clicked {count} times</p>
         <button onClick={() => setCount(count + 1)}>
           Click me
         </button>
       </div>
     );
   }
   ```

2. **useEffect:**
   - `useEffect` is used for side effects in functional components, such as data fetching, subscriptions, or manually changing the DOM.
   ```jsx
   import React, { useState, useEffect } from 'react';

   function Example() {
     const [count, setCount] = useState(0);

     useEffect(() => {
       document.title = `You clicked ${count} times`;
     }, [count]);

     return (
       <div>
         <p>You clicked {count} times</p>
         <button onClick={() => setCount(count + 1)}>
           Click me
         </button>
       </div>
     );
   }
   ```

3. **useContext:**
   - `useContext` is used to subscribe to React context without introducing nesting.
   ```jsx
   import React, { useContext } from 'react';

   const MyContext = React.createContext();

   function MyComponent() {
     const contextValue = useContext(MyContext);
     // ...
   }
   ```

4. **useReducer:**
   - `useReducer` is a hook for handling complex state logic. It's often preferable to `useState` when you have complex state logic that involves multiple sub-values or when the next state depends on the previous one.
   ```jsx
   import React, { useReducer } from 'react';

   function reducer(state, action) {
     switch (action.type) {
       case 'increment':
         return { count: state.count + 1 };
       case 'decrement':
         return { count: state.count - 1 };
       default:
         throw new Error();
     }
   }

   function Counter() {
     const [state, dispatch] = useReducer(reducer, { count: 0 });

     return (
       <>
         Count: {state.count}
         <button onClick={() => dispatch({ type: 'increment' })}>+</button>
         <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
       </>
     );
   }
   ```

These are just a few examples of the many hooks available. Hooks allow you to reuse stateful logic without changing your component hierarchy, making it easier to extract and share behaviors among components.

## Basic Components

In React Native, components are the building blocks of the user interface. Here are some basic components commonly used in React Native applications:

1. **View:**
   - The `View` component is like a `<div>` in web development. It's used to group other components together or to apply styles.
   ```jsx
   import { View, Text } from 'react-native';

   const MyComponent = () => (
     <View>
       <Text>Hello, React Native!</Text>
     </View>
   );
   ```

2. **Text:**
   - The `Text` component is used to display text.
   ```jsx
   import { Text } from 'react-native';

   const MyTextComponent = () => (
     <Text>Hello, React Native Text!</Text>
   );
   ```

3. **Image:**
   - The `Image` component is used to display images.
   ```jsx
   import { Image } from 'react-native';

   const MyImageComponent = () => (
     <Image
       source={{ uri: 'https://example.com/image.jpg' }}
       style={{ width: 200, height: 200 }}
     />
   );
   ```

4. **TextInput:**
   - The `TextInput` component is used to capture user input.
   ```jsx
   import { TextInput } from 'react-native';

   const MyInputComponent = () => (
     <TextInput
       placeholder="Type here..."
       onChangeText={(text) => console.log(text)}
     />
   );
   ```

5. **ScrollView:**
   - The `ScrollView` component is used for scrolling views.
   ```jsx
   import { ScrollView, Text } from 'react-native';

   const MyScrollView = () => (
     <ScrollView>
       <Text>Scroll me!</Text>
     </ScrollView>
   );
   ```

6. **FlatList:**
   - The `FlatList` component is used for rendering flat lists of data.
   ```jsx
   import { FlatList, Text } from 'react-native';

   const MyFlatList = () => (
     <FlatList
       data={[{ key: 'item1' }, { key: 'item2' }]}
       renderItem={({ item }) => <Text>{item.key}</Text>}
     />
   );
   ```

7. **TouchableOpacity:**
   - The `TouchableOpacity` component is used to create touchable elements.
   ```jsx
   import { TouchableOpacity, Text } from 'react-native';

   const MyTouchableComponent = () => (
     <TouchableOpacity onPress={() => console.log('Touchable pressed')}>
       <Text>Press me!</Text>
     </TouchableOpacity>
   );
   ```

## Using CSS in React-Native

In React Native, styling is done using a JavaScript-based styling system that is similar to CSS but has some differences. Here's how you can style components in React Native:

### Inline Styles:

You can use the `style` prop to apply styles directly to a component. The style is an object where keys are style property names, and values are the corresponding values.

```jsx
import React from 'react';
import { View, Text, StyleSheet } from 'react-native';

const MyComponent = () => {
  return (
    <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
      <Text style={{ fontSize: 20, color: 'blue' }}>Hello, React Native!</Text>
    </View>
  );
};

export default MyComponent;
```

### External Styles:

To keep your styles organized, you can define them in a separate JavaScript file and then import and apply them to your components.

**styles.js:**
```jsx
import { StyleSheet } from 'react-native';

export const commonStyles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
  },
  text: {
    fontSize: 20,
    color: 'blue',
  },
});
```

**MyComponent.js:**
```jsx
import React from 'react';
import { View, Text } from 'react-native';
import { commonStyles } from './styles';

const MyComponent = () => {
  return (
    <View style={commonStyles.container}>
      <Text style={commonStyles.text}>Hello, React Native!</Text>
    </View>
  );
};

export default MyComponent;
```

### Using Platform-Specific Styles:

You can apply styles conditionally based on the platform using the `Platform` module.

```jsx
import { Platform, StyleSheet } from 'react-native';

const styles = StyleSheet.create({
  text: {
    fontSize: 20,
    color: Platform.OS === 'ios' ? 'blue' : 'green',
  },
});
```

# Day 3
## How to do Navigation in React Native?
Navigation in React Native can be achieved using various navigation libraries. One of the most popular libraries is React Navigation. Here's a step-by-step guide on how to set up navigation in a React Native project using React Navigation.

### Step 1: Install React Navigation

Open your terminal and navigate to your React Native project. Run the following command to install the React Navigation library:

```bash
npm install @react-navigation/native
```

If you are using Expo, you also need to install the following dependencies:

```bash
expo install react-native-gesture-handler react-native-reanimated react-native-screens react-native-safe-area-context @react-native-community/masked-view
```

### Step 2: Choose a Navigator

React Navigation provides several navigators, each designed for different use cases:

- **Stack Navigator:** For a stack of screens where you can push and pop screens.
- **Drawer Navigator:** For a side menu navigation.
- **Tab Navigator:** For a bottom tab or top tab navigation.

Choose the navigator that fits your application's navigation structure. For this example, let's use a Stack Navigator.

### Step 3: Install Navigator Packages

Install the specific navigator package based on your choice. For the Stack Navigator:

```bash
npm install @react-navigation/stack
```

### Step 4: Set Up Navigation Container

In your main entry file (e.g., `App.js`), wrap your entire application with the `NavigationContainer`. This component is responsible for managing navigation state.

```jsx
// App.js
import React from 'react';
import { NavigationContainer } from '@react-navigation/native';
import { createStackNavigator } from '@react-navigation/stack';

import HomeScreen from './screens/HomeScreen';
import DetailsScreen from './screens/DetailsScreen';

const Stack = createStackNavigator();

const App = () => {
  return (
    <NavigationContainer>
      <Stack.Navigator>
        <Stack.Screen name="Home" component={HomeScreen} />
        <Stack.Screen name="Details" component={DetailsScreen} />
      </Stack.Navigator>
    </NavigationContainer>
  );
};

export default App;
```

### Step 5: Create Screens

Create your individual screens. In this example, we have `HomeScreen` and `DetailsScreen`.

```jsx
// HomeScreen.js
import React from 'react';
import { View, Text, Button } from 'react-native';

const HomeScreen = ({ navigation }) => {
  return (
    <View>
      <Text>Home Screen</Text>
      <Button
        title="Go to Details"
        onPress={() => navigation.navigate('Details')}
      />
    </View>
  );
};

export default HomeScreen;
```

```jsx
// DetailsScreen.js
import React from 'react';
import { View, Text } from 'react-native';

const DetailsScreen = () => {
  return (
    <View>
      <Text>Details Screen</Text>
    </View>
  );
};

export default DetailsScreen;
```

### Step 6: Navigate Between Screens

Now, you can use the `navigation` prop in your components to navigate between screens. In the `HomeScreen` component, pressing the "Go to Details" button will navigate to the `DetailsScreen`.

### Step 7: Customize Navigation

You can customize your navigation options, headers, and more using the options provided by the navigation library.

## Nested Navigation in React Native
Nested navigation in React Native refers to the concept of having multiple levels of navigation within your app. This often involves using different navigators for different parts of your application. The most common approach is to nest navigators inside each other.

Let's consider a scenario where you have a Stack Navigator for the main flow of your app, and within one of the screens, you want to have a Tab Navigator for additional navigation options.

Here's a step-by-step guide on how to achieve nested navigation using React Navigation:

### Step 1: Install React Navigation

Make sure you have React Navigation and the necessary dependencies installed in your project. You can follow the installation steps mentioned in the previous responses.

### Step 2: Set Up Main Stack Navigator

Create a Stack Navigator for the main flow of your app. This is typically done in your main entry file (`App.js` or `index.js`).

```jsx
// App.js
import React from 'react';
import { NavigationContainer } from '@react-navigation/native';
import { createStackNavigator } from '@react-navigation/stack';

import HomeScreen from './screens/HomeScreen';
import MainTabNavigator from './navigation/MainTabNavigator';

const Stack = createStackNavigator();

const App = () => {
  return (
    <NavigationContainer>
      <Stack.Navigator>
        <Stack.Screen name="Home" component={HomeScreen} />
        <Stack.Screen name="MainTabs" component={MainTabNavigator} />
      </Stack.Navigator>
    </NavigationContainer>
  );
};

export default App;
```

### Step 3: Create Main Tab Navigator

Create a Tab Navigator for the main content of your app. This could include tabs for different sections or features.

```jsx
// MainTabNavigator.js
import React from 'react';
import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';

import TabScreen1 from '../screens/TabScreen1';
import TabScreen2 from '../screens/TabScreen2';

const Tab = createBottomTabNavigator();

const MainTabNavigator = () => {
  return (
    <Tab.Navigator>
      <Tab.Screen name="Tab1" component={TabScreen1} />
      <Tab.Screen name="Tab2" component={TabScreen2} />
    </Tab.Navigator>
  );
};

export default MainTabNavigator;
```

### Step 4: Create Tab Screens

Create the individual screens for each tab in the Tab Navigator.

```jsx
// TabScreen1.js
import React from 'react';
import { View, Text } from 'react-native';

const TabScreen1 = () => {
  return (
    <View>
      <Text>Tab Screen 1</Text>
    </View>
  );
};

export default TabScreen1;
```

```jsx
// TabScreen2.js
import React from 'react';
import { View, Text } from 'react-native';

const TabScreen2 = () => {
  return (
    <View>
      <Text>Tab Screen 2</Text>
    </View>
  );
};

export default TabScreen2;
```

### Step 5: Navigate to Nested Navigator

Now, in your `HomeScreen` or any other screen within the main stack, you can navigate to the nested Tab Navigator.

```jsx
// HomeScreen.js
import React from 'react';
import { View, Text, Button } from 'react-native';

const HomeScreen = ({ navigation }) => {
  return (
    <View>
      <Text>Home Screen</Text>
      <Button
        title="Go to Main Tabs"
        onPress={() => navigation.navigate('MainTabs')}
      />
    </View>
  );
};

export default HomeScreen;
```

With this setup, you have a nested navigation structure where you navigate from the main stack to a Tab Navigator. You can further customize and expand this structure based on the needs of your application.

# Day 7

## State Management

### UseState Hook

In React Native, the `useState` hook is used in the same way as in React for managing state in functional components. The `useState` hook allows you to add state to your functional components without converting them to class components. Here's a simple example of how to use `useState` in a React Native functional component:

```jsx
import React, { useState } from 'react';
import { View, Text, Button } from 'react-native';

const ExampleComponent = () => {
  // The useState hook returns an array with two elements:
  // 1. The current state value.
  // 2. A function that allows you to update the state.
  const [count, setCount] = useState(0);

  const incrementCount = () => {
    setCount(count + 1);
  };

  const decrementCount = () => {
    setCount(count - 1);
  };

  return (
    <View>
      <Text>Count: {count}</Text>
      <Button title="Increment" onPress={incrementCount} />
      <Button title="Decrement" onPress={decrementCount} />
    </View>
  );
};

export default ExampleComponent;
```

In this example:

- We import `useState` from React.
- Inside the component, we use `useState(0)` to initialize the state variable `count` with an initial value of 0.
- The `setCount` function returned by `useState` is used to update the state.
- We have two buttons that, when pressed, call functions to increment or decrement the count.

Remember that the argument passed to `useState` is the initial state value. The return value from `useState` is an array with two elements: the current state value and a function to update the state.

You can use multiple `useState` hooks in a single component to manage different pieces of state independently. The state is retained between renders, and when the state is updated, the component re-renders with the new state values.

### Context API

React Native, just like React for web, supports the Context API for managing state at a global level and passing it down to components without using prop drilling. Here's a simple example of how to use the Context API in a React Native application:

1. **Create a Context:**
   Define a context using `React.createContext()` and provide a default value.

   ```jsx
   // MyContext.js
   import React, { createContext, useState } from 'react';

   const MyContext = createContext();

   const MyProvider = ({ children }) => {
     const [value, setValue] = useState('');

     return (
       <MyContext.Provider value={{ value, setValue }}>
         {children}
       </MyContext.Provider>
     );
   };

   export { MyContext, MyProvider };
   ```

2. **Wrap Your App with the Provider:**
   Wrap your entire app with the `MyProvider` to make the context available to all components.

   ```jsx
   // App.js
   import React from 'react';
   import { MyProvider } from './MyContext';
   import MyApp from './MyApp'; // Your main app component

   const App = () => {
     return (
       <MyProvider>
         <MyApp />
       </MyProvider>
     );
   };

   export default App;
   ```

3. **Use the Context in Components:**
   Consume the context in your components using the `useContext` hook.

   ```jsx
   // SomeComponent.js
   import React, { useContext } from 'react';
   import { MyContext } from './MyContext';

   const SomeComponent = () => {
     const { value, setValue } = useContext(MyContext);

     return (
       <div>
         <p>{value}</p>
         <button onClick={() => setValue('New Value')}>Change Value</button>
       </div>
     );
   };

   export default SomeComponent;
   ```

Now, any component within the `MyProvider` will have access to the state provided by the context. When the state is updated using `setValue` in one component, all other components consuming the context will re-render with the updated state.

Remember that this is a simplified example, and you may need to adapt it based on your specific use case. The Context API is useful for managing global state, avoiding prop drilling, and making state accessible across different parts of your React Native application.

### Redux 

Using Redux in React Native involves integrating the Redux library into your project, creating actions, reducers, and connecting components to the Redux store. Here's a step-by-step guide on how to set up Redux in a React Native application:

### Step 1: Install Redux and React-Redux

```bash
npm install redux react-redux
```

### Step 2: Create Actions

Create action types and action creators. Actions describe the type of change to be made and are typically defined as constants.

```jsx
// actions.js
export const INCREMENT = 'INCREMENT';
export const DECREMENT = 'DECREMENT';

export const increment = () => ({
  type: INCREMENT,
});

export const decrement = () => ({
  type: DECREMENT,
});
```

### Step 3: Create Reducers

Create reducers to handle the state changes based on the actions dispatched. Reducers are functions that take the current state and an action as arguments and return the new state.

```jsx
// reducers.js
import { INCREMENT, DECREMENT } from './actions';

const initialState = {
  count: 0,
};

const counterReducer = (state = initialState, action) => {
  switch (action.type) {
    case INCREMENT:
      return { count: state.count + 1 };
    case DECREMENT:
      return { count: state.count - 1 };
    default:
      return state;
  }
};

export default counterReducer;
```

### Step 4: Create the Redux Store

Combine reducers and create the Redux store.

```jsx
// store.js
import { createStore } from 'redux';
import counterReducer from './reducers';

const store = createStore(counterReducer);

export default store;
```

### Step 5: Wrap Your App with the Provider

Wrap your entire app with the `Provider` component from `react-redux` to make the Redux store available to all components.

```jsx
// App.js
import React from 'react';
import { Provider } from 'react-redux';
import store from './store';
import MyApp from './MyApp'; // Your main app component

const App = () => {
  return (
    <Provider store={store}>
      <MyApp />
    </Provider>
  );
};

export default App;
```

### Step 6: Connect Components

Connect the components that need access to the Redux store using the `connect` function from `react-redux`.

```jsx
// CounterComponent.js
import React from 'react';
import { connect } from 'react-redux';
import { increment, decrement } from './actions';

const CounterComponent = ({ count, increment, decrement }) => {
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
    </div>
  );
};

const mapStateToProps = (state) => ({
  count: state.count,
});

const mapDispatchToProps = {
  increment,
  decrement,
};

export default connect(mapStateToProps, mapDispatchToProps)(CounterComponent);
```

Now, your `CounterComponent` can access the `count` state and dispatch `increment` and `decrement` actions.

This is a basic setup for using Redux in a React Native application. Depending on your application's complexity, you might also want to explore middleware, selectors, and other advanced Redux concepts. Additionally, consider using React hooks (like `useSelector` and `useDispatch` from `react-redux`) for functional components.

### Redux Toolkit

Redux Toolkit is a set of utility functions and abstractions to simplify the Redux development process. It includes the `createSlice` function, which makes it easy to define reducers and actions in a concise way. Here's how you can use Redux Toolkit in a React Native application:

### Step 1: Install Redux Toolkit

```bash
npm install @reduxjs/toolkit react-redux
```

### Step 2: Create a Slice

Create a slice using the `createSlice` function from Redux Toolkit. A slice contains both the reducer and the actions.

```jsx
// counterSlice.js
import { createSlice } from '@reduxjs/toolkit';

const counterSlice = createSlice({
  name: 'counter',
  initialState: {
    count: 0,
  },
  reducers: {
    increment: (state) => {
      state.count += 1;
    },
    decrement: (state) => {
      state.count -= 1;
    },
  },
});

export const { increment, decrement } = counterSlice.actions;
export default counterSlice.reducer;
```

### Step 3: Create the Redux Store

Create the Redux store using the `configureStore` function from Redux Toolkit. Import and include the reducer created by the slice.

```jsx
// store.js
import { configureStore } from '@reduxjs/toolkit';
import counterReducer from './counterSlice';

const store = configureStore({
  reducer: {
    counter: counterReducer,
  },
});

export default store;
```

### Step 4: Wrap Your App with the Provider

Wrap your entire app with the `Provider` component from `react-redux` to make the Redux store available to all components.

```jsx
// App.js
import React from 'react';
import { Provider } from 'react-redux';
import store from './store';
import MyApp from './MyApp'; // Your main app component

const App = () => {
  return (
    <Provider store={store}>
      <MyApp />
    </Provider>
  );
};

export default App;
```

### Step 5: Connect Components

Connect the components that need access to the Redux store using the `useDispatch` and `useSelector` hooks provided by `react-redux`.

```jsx
// CounterComponent.js
import React from 'react';
import { useDispatch, useSelector } from 'react-redux';
import { increment, decrement } from './counterSlice';

const CounterComponent = () => {
  const count = useSelector((state) => state.counter.count);
  const dispatch = useDispatch();

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => dispatch(increment())}>Increment</button>
      <button onClick={() => dispatch(decrement())}>Decrement</button>
    </div>
  );
};

export default CounterComponent;
```

Now, your `CounterComponent` can access the `count` state and dispatch `increment` and `decrement` actions using the Redux Toolkit. This setup simplifies the process of creating actions and reducers, making your Redux code more concise and maintainable.

### React Query For Server State Management

React Query is a library for managing, caching, and updating server state in React applications. While it's designed to work with React, it can also be used in React Native projects. Here's a basic guide on using React Query in a React Native application:

### Step 1: Install React Query

```bash
npm install react-query react-query/devtools react-query/react-native
```

### Step 2: Set Up a Query

Create a query function using the `useQuery` hook from React Query.

```jsx
// api.js
export const fetchData = async () => {
  // Your API call logic here
  const response = await fetch('https://api.example.com/data');
  const data = await response.json();
  return data;
};
```

### Step 3: Use the Query in a Component

Use the `useQuery` hook in your React Native component to fetch and display data.

```jsx
// MyComponent.js
import React from 'react';
import { View, Text, ActivityIndicator } from 'react-native';
import { useQuery } from 'react-query';
import { fetchData } from './api';

const MyComponent = () => {
  const { data, isLoading, isError } = useQuery('myQueryKey', fetchData);

  if (isLoading) {
    return <ActivityIndicator size="large" />;
  }

  if (isError) {
    return <Text>Error fetching data</Text>;
  }

  return (
    <View>
      <Text>Data: {data}</Text>
    </View>
  );
};

export default MyComponent;
```

In the above example:

- `useQuery` is used to fetch and manage data.
- The query key (`'myQueryKey'`) is a unique identifier for this specific query.
- The `fetchData` function is the asynchronous function that performs the data fetching.

### Step 4: Wrap Your App with QueryClientProvider

Wrap your entire app with the `QueryClientProvider` to make the `QueryClient` available to all components.

```jsx
// App.js
import React from 'react';
import { QueryClient, QueryClientProvider } from 'react-query';
import MyComponent from './MyComponent';

const queryClient = new QueryClient();

const App = () => {
  return (
    <QueryClientProvider client={queryClient}>
      <MyComponent />
    </QueryClientProvider>
  );
};

export default App;
```

### Step 5: Optional - React Query Devtools

Optionally, you can include React Query Devtools for easier debugging.

```jsx
// App.js
import React from 'react';
import { QueryClient, QueryClientProvider } from 'react-query';
import { ReactQueryDevtools } from 'react-query/devtools';
import MyComponent from './MyComponent';

const queryClient = new QueryClient();

const App = () => {
  return (
    <QueryClientProvider client={queryClient}>
      <MyComponent />
      <ReactQueryDevtools />
    </QueryClientProvider>
  );
};

export default App;
```

Now you have a basic setup for using React Query in a React Native application. Adjust the `fetchData` function according to your API, and you can use other features provided by React Query, such as mutations, invalidations, and more.

Certainly! Let's explore some additional features provided by React Query, including mutations, invalidations, and more.

### Mutations

Mutations in React Query are used for updating data on the server. Here's an example of how to use mutations:

1. **Define a Mutation Function:**

```jsx
// api.js
export const updateData = async (updatedData) => {
  // Your API update logic here
  const response = await fetch('https://api.example.com/update', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
    },
    body: JSON.stringify(updatedData),
  });

  const data = await response.json();
  return data;
};
```

2. **Use Mutation in a Component:**

```jsx
// MyComponent.js
import React from 'react';
import { View, Text, ActivityIndicator, Button } from 'react-native';
import { useQuery, useMutation } from 'react-query';
import { fetchData, updateData } from './api';

const MyComponent = () => {
  const { data, isLoading, isError, refetch } = useQuery('myQueryKey', fetchData);

  const mutation = useMutation(updateData, {
    onSuccess: () => {
      // Invalidate and refetch data after mutation is successful
      queryClient.invalidateQueries('myQueryKey');
      refetch();
    },
  });

  const handleUpdate = () => {
    // Call the mutation function with the updated data
    mutation.mutate({ updatedData: 'newData' });
  };

  if (isLoading) {
    return <ActivityIndicator size="large" />;
  }

  if (isError) {
    return <Text>Error fetching data</Text>;
  }

  return (
    <View>
      <Text>Data: {data}</Text>
      <Button title="Update Data" onPress={handleUpdate} />
    </View>
  );
};

export default MyComponent;
```

In this example, the `useMutation` hook is used to create a mutation. When the mutation is successful, it invalidates the query and triggers a refetch.

### Invalidations

React Query allows you to manually invalidate queries to force a refetch. This is useful in scenarios where you want to refresh data from the server.

```jsx
// MyComponent.js
import React from 'react';
import { View, Text, Button } from 'react-native';
import { useQuery, queryClient } from 'react-query';
import { fetchData } from './api';

const MyComponent = () => {
  const { data, isLoading, isError, refetch } = useQuery('myQueryKey', fetchData);

  const handleInvalidate = () => {
    // Manually invalidate the query
    queryClient.invalidateQueries('myQueryKey');
  };

  if (isLoading) {
    return <ActivityIndicator size="large" />;
  }

  if (isError) {
    return <Text>Error fetching data</Text>;
  }

  return (
    <View>
      <Text>Data: {data}</Text>
      <Button title="Invalidate and Refetch" onPress={handleInvalidate} />
    </View>
  );
};

export default MyComponent;
```

### Additional Features

React Query provides many more features, including:

- **Optimistic Updates:** You can update the UI optimistically before the server response comes back.
- **Query Invalidation and Refetching:** Manually trigger a refetch of a specific query or all queries.
- **Query Stale Time:** Set a time after which the data is considered stale, and a background fetch is triggered.
- **Query Polling:** Periodically refetch data from the server.

Explore the [official React Query documentation](https://react-query.tanstack.com/) for more details and advanced use cases.