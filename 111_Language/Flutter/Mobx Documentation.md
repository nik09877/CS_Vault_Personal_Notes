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

- **Computed-s** form the derived state of your application. They depend on other observables or `computed` for their value. Any time the depending-observables change, they will recompute their new value. Computed-s are also smart and **cache** their previous value. Only when the computed-value is different from the cached-value, will they fire notifications. This behavior is key to ensure the connected reactions don't execute unnecessarily.