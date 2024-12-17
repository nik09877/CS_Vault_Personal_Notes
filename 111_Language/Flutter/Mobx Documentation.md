# Observables

## Definition

- Observables form the _reactive state_ of your MobX Application.
- Reactive state = Core state (**Observables**) + Derived state (**Computed**)
- Derived state is computed from the core state.

## Observable

- An `Observable` is used to track a single value, either primitive or complex. 
- Whenever it changes value, it will fire a notification so that all connected reactions will re-execute.

```dart
abstract class CounterBase with Store {
  @observable
  int value = 0;
}
```

## Reactive Extensions

- You can convert plain `int`, 'double', `bool`, and `String` literals into an observable version with the `.obs()` extension method.

```dart
var name = ''.obs(); // infers ObservableString
var counter = 0.obs(); // infers ObservableInt
```

- You can toggle an internal value of `Observable<bool>` with `.toggle()`

```dart
var lights = true.obs();
lights.toggle(); // now lights.value is false
```

## Readonly

- Use this annotation, if you want your observable to be read-only and to be changed by `@actions` methods only.
- **Note:** Just don't forget to use it only on **private fields** , or else you will get errors.

```dart
abstract class CounterBase with Store {  
  @readonly  
  int _value = 0;  
  
  @action  
  void increment() {  
	_value++;  
  }  
}
```

## Computed

- **Computed-s** form the derived state of your application. 
- They depend on other observables or `computed` for their value. 
- Any time the depending-observables change, they will recompute their new value.
- Computed-s are also smart and **cache** their previous value. 
- Only when the computed-value is different from the cached-value, will they fire notifications. This behavior is key to ensure the connected reactions don't execute unnecessarily.
- 
```dart
abstract class _Contact with Store {  
	@observable  
	String first = 'Nikhil';  
	  
	@observable  
	String last = 'Mishra';  
	  
	@computed  
	String get fullName => '${first} ${last}';  
}
```

## ObservableList

- It tracks when items are added, removed or modified and notifies the observers. 
- You can couple this with the `@observable` annotation to also track when the list reference changes, eg: going from `null` to a list with values.
- **NOTE:** Whenever you are using `Observer` and need to pass `ObservableList` to Observer child, use `observableList.toList()` to tell your `Observer` to track your list mutations and pass it to child widget as a `List`

### Example 1

```dart
class Controller {
  final ObservableList<String> observableList = ObservableList<String>();
}

  Observer(builder: (_) {
            return SizedBox(
              child: ChildWidget(
                list: controller.observableList.toList(), // Mobx will detect mutations to observableList
              ),
            );
          }),
```

### Example 2

```dart
class TodoList = _TodoList with _$TodoList;

abstract class _TodoList with Store {
  @observable
  ObservableList<Todo> todos = ObservableList<Todo>();

  @computed
  ObservableList<Todo> get pendingTodos =>
      ObservableList.of(todos.where((todo) => todo.done != true));

  @computed
  ObservableList<Todo> get completedTodos =>
      ObservableList.of(todos.where((todo) => todo.done == true));

  @action
  void addTodo(String description) {
    final todo = Todo(description);
    todos.add(todo);
  }

  @action
  void removeTodo(Todo todo) {
    todos.removeWhere((x) => x == todo);
  }
}

```

## ObservableMap
- Similar to  `ObservableList`

## ObservableSet
-  Similar to `ObservableList`

## ObservableFuture

- The `ObservableFuture` is the reactive wrapper around a `Future`. 
- You can use it to show the UI under various states of a `Future`, from `pending` to `fulfilled` or `rejected`. 
- The `status`, `result` and `error` fields of an `ObservableFuture` are observable and can be consumed on the UI.

```dart

// github_store.dart
part 'github_store.g.dart';

class GithubStore = _GithubStore with _$GithubStore;

abstract class _GithubStore with Store {
  // ...
  
  // We are starting with an empty future to avoid a null check
  @observable
  ObservableFuture<List<Repository>> fetchReposFuture = emptyResponse;
  
  static ObservableFuture<List<Repository>> emptyResponse =
      ObservableFuture.value([]);

	@action  
	Future<List<Repository>> fetchRepos() async {  
		repositories = [];  
		final future = client.repositories.listUserRepositories(user).toList();  
		fetchReposFuture = ObservableFuture(future);  
		  
		return repositories = await future;  
	}  
	  
	@action  
	void setUser(String text) {  
		fetchReposFuture = emptyResponse;  
		user = text;  
	}

  // ...
}

// github_widgets.dart
class LoadingIndicator extends StatelessWidget {
  const LoadingIndicator(this.store);

  final GithubStore store;

  @override
  Widget build(BuildContext context) => Observer(
      builder: (_) => store.fetchReposFuture.status == FutureStatus.pending
          ? const LinearProgressIndicator()
          : Container());
}

```

## ObservableStream

- Similar to `ObservableFuture`, an **`ObservableStream`** provides a reactive wrapper around a `Stream`. 
- This gives an easy way to observe and re-render whenever there is new `data`, or `error` or a `status` change on the `ObservableStream`.


# Actions

- **Actions** are used to update the observables.
- Changes to the observables are only notified at the end of the action.
- Actions can call other actions. For such nested actions, the change-notifications will be sent when the top-most action completes.
- All the linked reactions (ones that depend on the observables mutated inside the action) are run only at the end of the action. 
-  If you mutate an observable that is being observed, outside of an action, MobX will throw an `Exception`
- `Async` actions are allowed . 

```dart

abstract class _Counter with Store {
  @observable
  int value = 0;

  @action
  void increment() {
    value++;
  }
}
```

# Reactions

- Reactions allow you to perform side-effects when observable state changes. 
- This is useful for logging, showing snackbars, API calls, or navigation.

## Types

### 1. `reaction`

 - `ReactionDisposer reaction<T>(T Function(Reaction) fn, void Function(T) effect)`
- Only the observables inside `fn()` are tracked and runs the `effect()` when the tracking function returns a different value. 

#### Example: 

```dart
@observable
String greeting = 'Hello World';  
  
final dispose = reaction((_) => greeting.value, (msg) => print(msg));  
  
greeting.value = 'Hello MobX'; // Cause a change  
  
// Done with the reaction()  
dispose();
```

### 2. `autorun`
- `ReactionDisposer autorun(Function(Reaction) fn)`
- Runs the reaction immediately and also on any change in the observables used inside `fn`.
- **Note**: Avoid putting UI-related logic inside `autorun` since it runs immediately.

#### Example: Logging Observable Changes
```dart
@override
void initState() {
  super.initState();
  autorun((_) {
    print('Current count: ${store.counter}');
  });
}
```

### 3. `when`

- Runs the side-effect **once** when a specific condition (based on observable state) becomes true.
- Ideal for triggering actions like navigation or showing alerts

#### Example: Navigation When Condition is Met
```dart
@override
void initState() {
  super.initState();
  when(
    (_) => store.isLoggedIn, // Condition
    () => Navigator.pushReplacementNamed(context, '/home'), // Side-effect
  );
}
```

### 4. `asyncWhen`

- An asynchronous version of `when`. It waits for a condition to become true and resolves the future.

#### Example: Waiting for a Condition

```dart
@override
void initState() {
  super.initState();
  asyncWhen(
    (_) => store.isDataLoaded, // Condition
  ).then((_) {
    Navigator.pushReplacementNamed(context, '/dashboard');
  });
}
```

## Key Differences Between Reaction Types

| Reaction Type | Runs Immediately? | Runs Multiple Times? | Asynchronous? | Use Case                                   |
| ------------- | ----------------- | -------------------- | ------------- | ------------------------------------------ |
| `reaction`    | No                | Yes                  | No            | Fine-grained response to specific changes. |
| `autorun`     | Yes               | Yes                  | No            | Monitoring all dependencies.               |
| `when`        | No                | No (Only once)       | No            | Triggering side-effects for conditions.    |
| `asyncWhen`   | No                | No (Only once)       | Yes           | Waiting for conditions asynchronously.     |

## Common Use Cases for Reactions

### 1. Snackbar Notifications
```dart
reaction<bool>(
  (_) => store.isOnline,
  (isOnline) {
    final messenger = ScaffoldMessenger.of(context);
    messenger.showSnackBar(SnackBar(
      content: Text(isOnline ? 'You\'re online' : 'You\'re offline'),
    ));
  },
);

```

---

### 2. API Calls on State Change
```dart
reaction<int>(
  (_) => store.selectedCategory,
  (category) async {
    await store.fetchItemsForCategory(category);
  },
);

```

---

### 3. Redirecting Based on Authentication Status
```dart
when(
  (_) => store.isAuthenticated,
  () => Navigator.pushReplacementNamed(context, '/dashboard'),
);

```

---

### 4. Debugging Observable State
```dart
autorun((_) {
  print('Current user: ${store.user.name}');
});

```


---

### 5. Waiting for Asynchronous Conditions
```dart
asyncWhen(
  (_) => store.hasDataLoaded,
).then((_) {
  Navigator.pushReplacementNamed(context, '/data-view');
});

```

## Best Practices

- **Dispose Reactions:** Always clean up reactions in widgets' `dispose` method to avoid memory leaks.
- **Use Context Safely:** If you need to use `BuildContext` in reactions, ensure it's valid during the lifecycle of the widget.
- **Avoid Heavy Logic in Reactions:** Keep the logic in reactions lightweight and delegate heavy operations to other functions.

# Observer

- Whenever the observables / computed values change, `Observer` rebuilds and renders.

### Note
- When using `MobX` in Flutter, the `Observer` widget's `builder` function only tracks observables directly **accessed in its immediate execution context**. 
- If an observable is read inside a **nested function**, it won't be tracked, and changes to the observable won't trigger a rebuild.

### Problem Example: Nested Observable Access

##### WRONG CODE
```dart
class CounterStore = _CounterStore with _$CounterStore;

abstract class _CounterStore with Store {
  @observable
  int count = 0;

  void increment() => count++;
}

class CounterWidget extends StatelessWidget {
  final CounterStore store = CounterStore();

  @override
  Widget build(BuildContext context) {
    return Observer(
      builder: (_) {
        // Observable is not accessed directly in the builder context
        void printCount() {
          print(store.count); // Observable used in a nested function
        }

        // Calling the nested function
        printCount();

        return Text('Count: ${store.count}');
      },
    );
  }
}

```

#### Expected Behavior:

- The `Observer` should rebuild when `store.count` changes.

#### Actual Behavior:

- The `Observer` **does not rebuild** because `store.count` is accessed **inside the nested function (`printCount`)**, and MobX cannot track it.

### Solution: Access Observables Directly
To ensure proper tracking, **dereference (read) the observable in the immediate execution context** of the `builder`.

##### Correct Code
```dart
class CounterWidget extends StatelessWidget {
  final CounterStore store = CounterStore();

  @override
  Widget build(BuildContext context) {
    return Observer(
      builder: (_) {
        // Access the observable directly in the builder context
        final currentCount = store.count;

        // Nested function now uses a captured variable
        void printCount() {
          print(currentCount);
        }

        // Calling the nested function
        printCount();

        return Text('Count: $currentCount');
      },
    );
  }
}

```