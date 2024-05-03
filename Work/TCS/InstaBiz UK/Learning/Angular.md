#TODO
1. Angular components
2. managing dynamic data
3. rendering dynamic templates
4. using conditionals and loop
5. event handling
6. property binding
7. parent child comm
8. deferrable views

# Components in Angular

Components are the foundational building blocks for any Angular application. 

### Defining a Component

Every component has the following core properties:

1. A `@Component`[decorator](https://www.typescriptlang.org/docs/handbook/decorators.html) that contains some configuration
2. An HTML template that controls what renders into the DOM
3. A [CSS selector](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors) that defines how the component is used in HTML
4. A TypeScript class with behaviors such as managing state, handling user input, or fetching data from a server.


Here is a simplified example of a **TodoListItem** component.

Example :

```ts

// todo-list-item.component.ts
@Component({
  standalone: true,
  selector: 'todo-list-item',
  templateUrl: './todo-list-item.component.html',
  styleUrl: ['./todo-list-item.component.css'],
})
export class TodoListItem {
  /* Component behavior is defined in here */
}
```


```html

<!-- todo-list-item.component.html -->
<li>(TODO) Read Angular Essentials Guide</li>
```

```css

/* todo-list-item.component.css */
li {
  color: red;
  font-weight: 300;
}

```

### Using a Component

One advantage of component architecture is that your application is modular. In other words, components can be used in other components.

To use a component, you need to use the component's selector in the `template`

Here's an example of a `TodoList` component importing the `TodoListItem` component from before:

```ts

// todo-list.component.ts
import {TodoListItem} from './todo-list-item.component.ts';
@Component({
  template: `
    <ul>
      <todo-list-item></todo-list-item>
    </ul>
  `,
})
export class TodoList {}
```


# Managing Dynamic Data

Define component state and behavior to manage dynamic data.

### What is state?

Components let you neatly encapsulate responsibility for discrete parts of your application. For example, a `SignUpForm` component might need to keep track of whether the form is valid or not before allowing users to take a specific action. As a result, the various properties that a component needs to track is often referred to as "state."