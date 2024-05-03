
# DAY 1

---

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

### Defining state

To define state, you use [class fields syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/Public_class_fields) inside of your component.

For example, using the `TodoListItem` component, create two properties that you want to track:

1. `taskTitle` — What the title of the task is
2. `isComplete` — Whether or not the task is complete

```ts
// todo-list-item.component.ts
@Component({ ... })
export class TodoListItem {
  taskTitle = '';
  isComplete = false;
}
```


### Updating state

When you want to update state, this is typically accomplished by defining methods in the component class that can access the various class fields with the `this` keyword.

```ts
// todo-list-item.component.ts
@Component({ ... })
export class TodoListItem {
  taskTitle = '';
  isComplete = false;
  completeTask() {
    this.isComplete = true;
  }
  updateTitle(newTitle: string) {
    this.taskTitle = newTitle;
  }
}
```

# Rendering Dynamic Templates

When you need to display dynamic content in your template, Angular uses the double curly brace syntax in order to distinguish between static and dynamic content.

Here is a simplified example from a `TodoListItem` component.

```ts
@Component({
  selector: 'todo-list-item',
  template: `
    <p>Title: {{ taskTitle }}</p>
  `,
})
export class TodoListItem {
  taskTitle = 'Read cup of coffee';
}
```

When Angular renders the component you'll see the output:

```html
<p>Title: Read cup of coffee</p>
```

This syntax declares an **interpolation** between the dynamic data property inside of the HTML. As a result, whenever the data changes, Angular will automatically update the DOM reflecting the new value of the property.

### Dynamic Properties

When you need to dynamically set the value of standard DOM properties on an HTML element, the property is wrapped in square brackets to inform Angular that the declared value should be interpreted as a JavaScript-like statement ([with some Angular enhancements](https://angular.dev/guide/templates/interpolation)) instead of a plain string.

For example, a common example of dynamically updating properties in your HTML is determining whether the form submit button should be disabled based on whether the form is valid or not.

Wrap the desired property in square brackets to tell Angular that the assigned value is dynamic (i.e., not a static string).

```ts
@Component({
  selector: 'sign-up-form',
  template: `
    <button type="submit" [disabled]="formIsInvalid">Submit</button>
  `,
})
export class SignUpForm {
  formIsInvalid = true;
}
```

In this example, because `formIsInvalid` is true, the rendered HTML would be:

```html
<button type="submit" disabled>Submit</button>
```

### Dynamic Attributes

In the event you want to dynamically bind custom HTML attributes (e.g., `aria-`, `data-`, etc.), you might be inclined to wrap the custom attributes with the same square brackets.

```ts
@Component({
  standalone: true,
  template: `
    <button [data-test-id]="testId">Primary CTA</button>
  `,
})
export class AppBanner {
  testId = 'main-cta';
}
```

Unfortunately, this will not work because custom HTML attributes are not standard DOM properties. In order for this to work as intended, we need to prepend the custom HTML attribute with the `attr.` prefix.

```ts
@Component({
  standalone: true,
  template: `
    <button [attr.data-test-id]="testId">Primary CTA</button>
  `,
})
export class AppBanner {
  testId = 'main-cta';
}
```

# Conditionals and Loops

Conditionally show and/or repeat content based on dynamic data

### Conditional rendering

One of the most common scenarios that developers encounter is the desire to show or hide content in templates based on a condition.

A common example of this is whether or not to display certain controls on the screen based on the user's permission level

#### `*ngif` block

Similar to JavaScript's `if` statement, Angular uses `*ngif` control flow blocks to conditionally hide and show part of a template and its contents.

```ts

// user-controls.component.ts
@Component({
  standalone: true,
  selector: 'user-controls',
  template: `
    <button *ngif="isAdmin==true">Erase database</button>
  `,
})
export class UserControls {
  isAdmin = true;
}
```



In this example, Angular only renders the `<button>` element if the `isAdmin` property is true. Otherwise, it does not appear on the page.

### Rendering a list

Another common scenario developers encounter is the need to render a list of items.

#### `*ngfor` block

Similar to JavaScript’s `for...of` loops, Angular provides the `*ngfor` block for rendering repeated elements.

```html
<!-- ingredient-list.component.html -->
<ul>
	<li *ngfor="let ingredient of ingredientList">{{ ingredient.quantity }} - {{ ingredient.name }}</li>
</ul>
```

```ts
// ingredient-list.component.ts
@Component({
  standalone: true,
  selector: 'ingredient-list',
  templateUrl: './ingredient-list.component.html',
})
export class IngredientList {
  ingredientList = [
    {name: 'noodles', quantity: 1},
    {name: 'miso broth', quantity: 1},
    {name: 'egg', quantity: 2},
  ];
}
```

# Event Handling

You can add an event handler to an element by:

1. Adding an attribute with the events name inside of parentheses
2. Specify what JavaScript statement you want to run when it fires

```html
<button (click)="save()">Save</button>
```

For example, if we wanted to create a button that would run a `transformText` function when the `click` event is fired, it would look like the following:

```ts
// text-transformer.component.ts
@Component({
  standalone: true,
  selector: 'text-transformer',
  template: `
    <p>{{ announcement }}</p>
    <button (click)="transformText()">Abracadabra!</button>
  `,
})
export class TextTransformer {
  announcement = 'Hello again Angular!';
  transformText() {
    this.announcement = this.announcement.toUpperCase();
  }
}
```

### $event

If you need to access the [event](https://developer.mozilla.org/en-US/docs/Web/API/Event) object, Angular provides an implicit `$event` variable that you can pass to a function:

```html
<button (click)="createUser($event)">Submit</button>
```


# Component Interaction

### Pass data from parent to child with `@input` binding

`HeroChildComponent` has two **_input properties_**, typically adorned with [@Input decorations](https://devdocs.io/angular~7/guide/template-syntax#inputs-outputs).

```ts
import { Component, Input } from '@angular/core';

import { Hero } from './hero';

@Component({
  selector: 'app-hero-child',
  template: `
    <h3>{{hero.name}} says:</h3>
    <p>I, {{hero.name}}, am at your service, {{masterName}}.</p>
  `
})
export class HeroChildComponent {
  @Input() hero: Hero;
  @Input('master') masterName: string;
}
```

The second @[Input](https://devdocs.io/angular~7/api/core/input) aliases the child component property name `'masterName'` as `'master'`.

The `HeroParentComponent` nests the child `HeroChildComponent` inside an *[ngFor](https://devdocs.io/angular~7/api/common/ngforof) repeater, binding its `master` string property to the child's `master` alias, and each iteration's `hero` instance to the child's `hero` property.

```ts
import { Component } from '@angular/core';

import { HEROES } from './hero';

@Component({
  selector: 'app-hero-parent',
  template: `
    <h2>{{master}} controls {{heroes.length}} heroes</h2>
    <app-hero-child *ngFor="let hero of heroes"
      [hero]="hero"
      [master]="master">
    </app-hero-child>
  `
})
export class HeroParentComponent {
  heroes = HEROES;
  master = 'Master';
}
```

### Parent listens for child event

The child component exposes an [EventEmitter](https://devdocs.io/angular~7/api/core/eventemitter) property with which it `emits` events when something happens. The parent binds to that event property and reacts to those events.

The child's [EventEmitter](https://devdocs.io/angular~7/api/core/eventemitter) property is an **_output property_**, typically adorned with an [@Output decoration](https://devdocs.io/angular~7/guide/template-syntax#inputs-outputs) as seen in this `VoterComponent`:

```ts
import { Component, EventEmitter, Input, Output } from '@angular/core';

@Component({
  selector: 'app-voter',
  template: `
    <h4>{{name}}</h4>
    <button (click)="vote(true)"  [disabled]="didVote">Agree</button>
    <button (click)="vote(false)" [disabled]="didVote">Disagree</button>
  `
})
export class VoterComponent {
  @Input()  name: string;
  @Output() voted = new EventEmitter<boolean>();
  didVote = false;

  vote(agreed: boolean) {
    this.voted.emit(agreed);
    this.didVote = true;
  }
}
```

Clicking a button triggers emission of a `true` or `false`, the boolean _payload_.

The parent `VoteTakerComponent` binds an event handler called `onVoted()` that responds to the child event payload `$event` and updates a counter.

```ts
import { Component }      from '@angular/core';

@Component({
  selector: 'app-vote-taker',
  template: `
    <h2>Should mankind colonize the Universe?</h2>
    <h3>Agree: {{agreed}}, Disagree: {{disagreed}}</h3>
    <app-voter *ngFor="let voter of voters"
      [name]="voter"
      (voted)="onVoted($event)">
    </app-voter>
  `
})
export class VoteTakerComponent {
  agreed = 0;
  disagreed = 0;
  voters = ['Mr. IQ', 'Ms. Universe', 'Bombasto'];

  onVoted(agreed: boolean) {
    agreed ? this.agreed++ : this.disagreed++;
  }
}
```

The framework passes the event argument—represented by `$event`—to the handler method, and the method processes it:


--- 

# DAY 2