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
# TO DO
functional components class components state lifecycle methods hooks basic components - text,text input,image,view,scroll view,list views, flat list etc.. styling - inline styles, stylesheets take a poc login page - username password Login- button apply styles to them add validations to username and password - username - email and password - 8 digits