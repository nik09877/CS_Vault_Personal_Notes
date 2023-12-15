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
## Responsive Design
- up to 300 small mobiles 
- 300 - 600 mobiles
- 600 - 800 tabs
- 800 + desktop
