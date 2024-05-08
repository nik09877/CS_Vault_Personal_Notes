
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

# Routing & Navigation

The Angular [Router](https://devdocs.io/angular~7/api/router/router) enables navigation from one [view](https://devdocs.io/angular~7/guide/glossary#view) to the next as users perform application tasks.

## The Basics

### `<base href>`
Most routing applications should add a `<base>` element to the `index.html` as the first child in the `<head>` tag to tell the router how to compose navigation URLs.

If the `app` folder is the application root, as it is for the sample application, set the [href](https://devdocs.io/angular~7/api/router/routerlinkwithhref#href) value _exactly_ as shown below.

```html
<base href="/">
```

### Router imports

The Angular Router is an optional service that presents a particular component view for a given URL.
```ts
import { RouterModule, Routes } from '@angular/router';
```

### Configuration

A routed Angular application has one singleton instance of the _[Router](https://devdocs.io/angular~7/api/router/router)_ service. When the browser's URL changes, that router looks for a corresponding [Route](https://devdocs.io/angular~7/api/router/route) from which it can determine the component to display.

A router has no routes until you configure it. The following example creates five route definitions, configures the router via the [RouterModule.forRoot()](https://devdocs.io/angular~7/api/router/routermodule#forRoot) method, and adds the result to the `AppModule`'s `imports` array.

```ts
const appRoutes: Routes = [
  { path: 'crisis-center', component: CrisisListComponent },
  { path: 'hero/:id',      component: HeroDetailComponent },
  {
    path: 'heroes',
    component: HeroListComponent,
    data: { title: 'Heroes List' }
  },
  { path: '',
    redirectTo: '/heroes',
    pathMatch: 'full'
  },
  { path: '**', component: PageNotFoundComponent }
];

@NgModule({
  imports: [
    RouterModule.forRoot(
      appRoutes,
      { enableTracing: true } // <-- debugging purposes only
    )
    // other imports here
  ],
  ...
})
export class AppModule { }
```

- The `appRoutes` array of _routes_ describes how to navigate. Pass it to the [RouterModule.forRoot()](https://devdocs.io/angular~7/api/router/routermodule#forRoot) method in the module `imports` to configure the router.

- Each [Route](https://devdocs.io/angular~7/api/router/route) maps a URL `path` to a component. 

- The `:id` in the second route is a token for a route parameter. In a URL such as `/hero/42`, "42" is the value of the `id` parameter. 

- The `data` property in the third route is a place to store arbitrary data associated with this specific route. The data property is accessible within each activated route. Use it to store items such as page titles, breadcrumb text, and other read-only, _static_ data. You'll use the [resolve guard](https://devdocs.io/angular~7/guide/router#resolve-guard) to retrieve _dynamic_ data later in the guide.

- The **empty path** in the fourth route represents the default path for the application. This default route redirects to the route for the `/heroes` URL and, therefore, will display the `HeroesListComponent`.

- The `**` path in the last route is a **wildcard**. The router will select this route if the requested URL doesn't match any paths for routes defined earlier in the configuration. This is useful for displaying a "404 - Not Found" page.

- **The order of the routes in the configuration matters** and this is by design. The router uses a **first-match wins** strategy when matching routes, so more specific routes should be placed above less specific routes.

- If you need to see what events are happening during the navigation lifecycle, there is the **enableTracing** option as part of the router's default configuration.

### Router outlet

The [RouterOutlet](https://devdocs.io/angular~7/api/router/routeroutlet) is a directive from the router library that is used like a component. It acts as a placeholder that marks the spot in the template where the router should display the components for that outlet.

```html
<router-outlet></router-outlet>
  <!-- Routed components go here -->
```

### Router links

The [RouterLink](https://devdocs.io/angular~7/api/router/routerlink) directives on the anchor tags give the router control over those elements. The navigation paths are fixed, so you can assign a string to the [routerLink](https://devdocs.io/angular~7/api/router/routerlink) (a "one-time" binding).

Had the navigation path been more dynamic, you could have bound to a template expression that returned an array of route link parameters (the _link parameters array_). The router resolves that array into a complete URL.

```html
<h1>Angular Router</h1>
<nav>
  <a routerLink="/crisis-center" routerLinkActive="active">Crisis Center</a>
  <a routerLink="/heroes" routerLinkActive="active">Heroes</a>
</nav>
<router-outlet></router-outlet>
```

### Router state

- After the end of each successful navigation lifecycle, the router builds a tree of [ActivatedRoute](https://devdocs.io/angular~7/api/router/activatedroute) objects that make up the current state of the router.

- Each [ActivatedRoute](https://devdocs.io/angular~7/api/router/activatedroute) in the [RouterState](https://devdocs.io/angular~7/api/router/routerstate) provides methods to traverse up and down the route tree to get information from parent, child and sibling routes.

### Activated route

The route path and parameters are available through an injected router service called the [ActivatedRoute](https://devdocs.io/angular~7/api/router/activatedroute). It has a great deal of useful information including:

| Property        | Description                                                                                                                                                                                                                                                                                                   |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `url`           | An `Observable` of the route path(s), represented as an array of strings for each part of the route path.                                                                                                                                                                                                     |
| `data`          | An `Observable` that contains the `data` object provided for the route. Also contains any resolved values from the [resolve guard](https://devdocs.io/angular~7/guide/router#resolve-guard).                                                                                                                  |
| `paramMap`      | An `Observable` that contains a [map](https://devdocs.io/angular~7/api/router/parammap) of the required and [optional parameters](https://devdocs.io/angular~7/guide/router#optional-route-parameters) specific to the route. The map supports retrieving single and multiple values from the same parameter. |
| `queryParamMap` | An `Observable` that contains a [map](https://devdocs.io/angular~7/api/router/parammap) of the [query parameters](https://devdocs.io/angular~7/guide/router#query-parameters) available to all routes. The map supports retrieving single and multiple values from the query parameter.                       |
| `fragment`      | An `Observable` of the URL [fragment](https://devdocs.io/angular~7/guide/router#fragment) available to all routes.                                                                                                                                                                                            |
| `outlet`        | The name of the [RouterOutlet](https://devdocs.io/angular~7/api/router/routeroutlet) used to render the route. For an unnamed outlet, the outlet name is _primary_.                                                                                                                                           |
| `routeConfig`   | The route configuration used for the route that contains the origin path.                                                                                                                                                                                                                                     |
| `parent`        | The route's parent [ActivatedRoute](https://devdocs.io/angular~7/api/router/activatedroute) when this route is a [child route](https://devdocs.io/angular~7/guide/router#child-routing-component).                                                                                                            |
| `firstChild`    | Contains the first [ActivatedRoute](https://devdocs.io/angular~7/api/router/activatedroute) in the list of this route's child routes.                                                                                                                                                                         |
| `children`      | Contains all the [child routes](https://devdocs.io/angular~7/guide/router#child-routing-component) activated under the current route.                                                                                                                                                                         |

# Reactive Forms

_Reactive forms_ provide a model-driven approach to handling form inputs whose values change over time

## Getting started

### Step 1: Registering the reactive forms module

To use reactive forms, import [ReactiveFormsModule](https://devdocs.io/angular~7/api/forms/reactiveformsmodule) from the `@angular/forms` package and add it to your NgModule's `imports` array.

```ts
import { ReactiveFormsModule } from '@angular/forms';

@NgModule({
  imports: [
    // other imports ...
    ReactiveFormsModule
  ],
})
export class AppModule { }
```

### Step 2: Generating and importing a new form control

The [FormControl](https://devdocs.io/angular~7/api/forms/formcontrol) class is the basic building block when using reactive forms. To register a single form control, import the [FormControl](https://devdocs.io/angular~7/api/forms/formcontrol) class into your component and create a new instance of the form control to save as a class property.

```ts
import { Component } from '@angular/core';
import { FormControl } from '@angular/forms';

@Component({
  selector: 'app-name-editor',
  templateUrl: './name-editor.component.html',
  styleUrls: ['./name-editor.component.css']
})
export class NameEditorComponent {
  name = new FormControl('');
}
```

### Step 3: Registering the control in the template

After you create the control in the component class, you must associate it with a form control element in the template. Update the template with the form control using the `formControl` binding provided by [FormControlDirective](https://devdocs.io/angular~7/api/forms/formcontroldirective) included in [ReactiveFormsModule](https://devdocs.io/angular~7/api/forms/reactiveformsmodule).

```html
<label>
  Name:
  <input type="text" [formControl]="name">
</label>
```

## Managing control values

### Displaying a form control value

You can display the value in these ways:

- Through the `valueChanges` observable where you can listen for changes in the form's value in the template using `[AsyncPipe](https://devdocs.io/angular~7/api/common/asyncpipe)` or in the component class using the `subscribe()` method.
- With the `value` property. which gives you a snapshot of the current value.

```html
<p>
  Value: {{ name.value }}
</p>
```

### Replacing a form control value

A form control instance provides a `setValue()` method that updates the value of the form control and validates the structure of the value provided against the control's structure.

```ts
updateName() {
  this.name.setValue('Nancy');
}
```

## Grouping form controls

A form group instance tracks the form state of a group of form control instances. Each control in a form group instance is tracked by name when creating the form group.

### Step 1: Creating a FormGroup instance

Create a property in the component class named `profileForm` and set the property to a new form group instance. To initialize the form group, provide the constructor with an object of named keys mapped to their control.

For the profile form, add two form control instances with the names `firstName` and `lastName`.

```ts
import { Component } from '@angular/core';
import { FormGroup, FormControl } from '@angular/forms';

@Component({
  selector: 'app-profile-editor',
  templateUrl: './profile-editor.component.html',
  styleUrls: ['./profile-editor.component.css']
})
export class ProfileEditorComponent {
  profileForm = new FormGroup({
    firstName: new FormControl(''),
    lastName: new FormControl(''),
  });
}
```

### Step 2: Associating the FormGroup model and view

A form group tracks the status and changes for each of its controls, so if one of the controls changes, the parent control also emits a new status or value change. The model for the group is maintained from its members. After you define the model, you must update the template to reflect the model in the view.

```html
<form [formGroup]="profileForm" (ngSubmit)="onSubmit()">
  
  <label>
    First Name:
    <input type="text" formControlName="firstName">
  </label>

  <label>
    Last Name:
    <input type="text" formControlName="lastName">
  </label>

</form>
```

### Saving form data

The [FormGroup](https://devdocs.io/angular~7/api/forms/formgroup) directive listens for the `submit` event emitted by the `form` element and emits an `ngSubmit` event that you can bind to a callback function.

Add an `ngSubmit` event listener to the `form` tag with the `onSubmit()` callback method.

```html
<form [formGroup]="profileForm" (ngSubmit)="onSubmit()">

<button type="submit" [disabled]="!profileForm.valid">Submit</button>
```


# Template Driven Forms

Template-driven forms in Angular are one of the two ways of building forms in Angular, the other being reactive forms. Template-driven forms allow you to specify the form's behaviors and validations using directives and attributes directly in the HTML template, with minimal code required in the component class. [2](https://www.scaler.com/topics/angular/template-driven-forms-in-angular/)[3](https://angular.io/guide/forms)The key points about template-driven forms in Angular are:

1. The `FormsModule` needs to be imported in the application module to use template-driven forms. [3](https://angular.io/guide/forms)
2. The `ngForm` directive is used to convert the HTML form into an Angular form, creating a top-level `FormGroup` control. [2](https://www.scaler.com/topics/angular/template-driven-forms-in-angular/)[3](https://angular.io/guide/forms)
3. The `ngModel` directive is used to create `FormControl` instances for each form element, enabling two-way data binding. [2](https://www.scaler.com/topics/angular/template-driven-forms-in-angular/)[3](https://angular.io/guide/forms)
4. Validations are configured directly in the template using directives and attributes, without needing to write validation logic in the component class. [2](https://www.scaler.com/topics/angular/template-driven-forms-in-angular/)[3](https://angular.io/guide/forms)
5. Template-driven forms are simpler to set up compared to reactive forms, but they can be more challenging to unit test and add controls dynamically.

```html
<form #myForm="ngForm" (ngSubmit)="onSubmit(myForm)">

  <div>

    <label for="name">Name:</label>

    <input type="text" id="name" name="name" [(ngModel)]="name" required />

    <div

      *ngIf="myForm.controls.name?.invalid && (myForm.controls.name?.dirty || myForm.controls.name?.touched)"

    >

      Name is required.

    </div>

  </div>

  <div>

    <label for="email">Email:</label>

    <input

      type="email"

      id="email"

      name="email"

      [(ngModel)]="email"

      required

      email

    />

    <div

      *ngIf="myForm.controls.email?.invalid && (myForm.controls.email?.dirty || myForm.controls.email?.touched)"

    >

      Please enter a valid email address.

    </div>

  </div>

  <button type="submit" [disabled]="myForm.invalid">Submit</button>

</form>
```

```ts
import { Component } from '@angular/core';

import { NgForm } from '@angular/forms';

@Component({

  selector: 'app-root',

  templateUrl: './app.component.html',

  styleUrls: ['./app.component.css'],

})

export class AppComponent {

  name: string;

  email: string;

  onSubmit(form: NgForm) {

    console.log('Form submitted:', form.value);

  }

}
```

# HttpClient

In Angular, we can use the `HttpClient` module to make API calls. 

1. **Import HttpClientModule**: First, you need to import `HttpClientModule` in your Angular module. Typically, this is done in your `AppModule` (or other feature module) file (`app.module.ts`)

```ts
import { HttpClientModule } from '@angular/common/http';

@NgModule({
  imports: [
    HttpClientModule
  ],
  // Other configurations...
})
export class AppModule { }

```

2. **Inject HttpClient**: Next, you'll need to inject `HttpClient` into your Angular service or component where you want to make API calls. For example, in your service:

```ts
import { HttpClient } from '@angular/common/http';
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class DataService {

  constructor(private http: HttpClient) { }

  // Your API call methods will go here
}

```

3. **Make API Calls**: Now, you can use the `HttpClient` instance to make API calls. You typically use methods like `get`, `post`, `put`, `delete`, etc. Here's an example of making a GET request:

```ts
import { HttpClient } from '@angular/common/http';
import { Injectable } from '@angular/core';
import { Observable } from 'rxjs';

@Injectable({
  providedIn: 'root'
})
export class DataService {

  constructor(private http: HttpClient) { }

  fetchData(): Observable<any> {
    return this.http.get<any>('https://api.example.com/data');
  }
}

```

4. **Handle Responses**: You can subscribe to the observable returned by the HTTP request to handle the response. For example:

```ts
import { Component, OnInit } from '@angular/core';
import { DataService } from './data.service';

@Component({
  selector: 'app-example',
  templateUrl: './example.component.html',
  styleUrls: ['./example.component.css']
})
export class ExampleComponent implements OnInit {

  constructor(private dataService: DataService) { }

  ngOnInit(): void {
    this.dataService.fetchData().subscribe((data) => {
      console.log(data); // Handle response data here
    }, (error) => {
      console.error('Error fetching data:', error); // Handle errors here
    });
  }
}
```

# Services

In Angular, services are classes that are responsible for encapsulating reusable logic and functionality that can be shared across different parts of your application. Services provide a way to keep your code modular, maintainable, and easier to test. They are typically used for tasks such as data retrieval, business logic, and communication with external APIs.

Here's how you can create and use a service in Angular:

1. **Creating a Service**:
You can create a service using Angular CLI's `ng generate service` command or manually create a TypeScript class. Let's manually create a service:

```bash
ng generate service my-service
```

This will generate a service file (`my-service.service.ts`) and add it to the `app` folder in your Angular project.

```ts
// my-service.service.ts

import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class MyService {

  constructor() { }

  // Define methods and functionality here
}

```

The `@Injectable` decorator marks the class as a service and allows it to be injected into other components or services.

2. **Using the Service**:
You can now inject the service into any component or other service where you want to use its functionality. Angular's dependency injection system will handle the instantiation and management of the service instance.

```ts
// example.component.ts

import { Component, OnInit } from '@angular/core';
import { MyService } from './my-service.service';

@Component({
  selector: 'app-example',
  templateUrl: './example.component.html',
  styleUrls: ['./example.component.css']
})
export class ExampleComponent implements OnInit {

  constructor(private myService: MyService) { }

  ngOnInit(): void {
    // Use service methods here
  }
}

```

3. **Using Service Methods**:
Within your component, you can call methods defined in the service as you would with any other class method.

```ts
// example.component.ts

import { Component, OnInit } from '@angular/core';
import { MyService } from './my-service.service';

@Component({
  selector: 'app-example',
  templateUrl: './example.component.html',
  styleUrls: ['./example.component.css']
})
export class ExampleComponent implements OnInit {

  constructor(private myService: MyService) { }

  ngOnInit(): void {
    this.myService.doSomething(); // Call a method defined in the service
  }
}
```

```ts
// my-service.service.ts

import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class MyService {

  constructor() { }

  doSomething() {
    console.log('Doing something...');
  }
}
```

4. **Providing the Service**:

The `providedIn: 'root'` option in the `@Injectable` decorator allows Angular to optimize the service by providing it at the root level. This makes it available throughout your application without the need to import it into specific modules.

Alternatively, you can provide the service in a specific module by importing it into the module and adding it to the `providers` array:

```ts
// app.module.ts

import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { MyService } from './my-service.service'; // Import the service

@NgModule({
  declarations: [
    // Components and directives
  ],
  imports: [
    BrowserModule,
    // Other modules
  ],
  providers: [MyService], // Provide the service here
  bootstrap: [AppComponent]
})
export class AppModule { }

```

---
# DAY 3

# Pipes

In Angular, pipes are a feature that allows you to transform data in your templates before displaying it to the user.

### Built-in Pipes in Angular:

1. **DatePipe**: Formats a date value according to locale rules.

```html
<p>{{ currentDate | date }}</p>
```

2. **UpperCasePipe**: Transforms text to all uppercase.

```html
<p>{{ text | uppercase }}</p>
```

3. **LowerCasePipe**: Transforms text to all lowercase.

```html
<p>{{ text | lowercase }}</p>
```

4. **CurrencyPipe**: Formats a number as currency using locale rules.

```html
<p>{{ price | currency }}</p>
```

5. **DecimalPipe**: Formats a number as decimal number according to locale rules.

```html
<p>{{ number | number:'1.2-3' }}</p>
```

6. **PercentPipe**: Formats a number as a percentage.

```html
<p>{{ percentage | percent }}</p>
```

### Creating Custom Pipes:

To create a custom pipe, you need to use the `@Pipe` decorator and implement the `PipeTransform` interface.

```ts
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'custom'
})
export class CustomPipe implements PipeTransform {

  transform(value: any, args?: any): any {
    // Custom transformation logic
    return transformedValue;
  }
}

```

#### Example of Custom Pipe:

Let's create a custom pipe that appends a given string to the input value.

```ts
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'append'
})
export class AppendPipe implements PipeTransform {

  transform(value: any, appendValue: string): any {
    if (!value) return '';
    return value + appendValue;
  }
}

```

```ts
<p>{{ 'Hello' | append:' World' }}</p>
```

### Types of Pipes in Angular:

1. **Pure Pipes**: Pure pipes only recalculate the output when a pure change to the input value is detected. Pure changes are either changes to primitive input values (String, Number, Boolean) or changes to object references. Pure pipes are more performant and are the default type of pipe.
    
2. **Impure Pipes**: Impure pipes recalculate the output on every change detection cycle, regardless of whether the input value has changed. Impure pipes should be used with caution as they can impact performance negatively.

### Pure Pipe Example:

```ts
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'multiply'
})
export class MultiplyPipe implements PipeTransform {

  transform(value: number, multiplier: number): number {
    return value * multiplier;
  }
}

```

In this example, we have created a pure pipe called `MultiplyPipe` that multiplies a number by a given multiplier. Since this pipe only depends on its input values (`value` and `multiplier`), it is pure.

You can use this pipe in your template like this:

```html
<p>{{ 5 | multiply: 2 }}</p>
```

### Impure Pipe Example:

```ts
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'randomNumber',
  pure: false
})
export class RandomNumberPipe implements PipeTransform {

  transform(): number {
    return Math.random();
  }
}

```

In this example, we have created an impure pipe called `RandomNumberPipe` that generates a random number. Since this pipe does not depend on its input values and generates a new random number on each change detection cycle, it is impure.

You can use this pipe in your template like this:

```html
<p>{{ 'Random Number: ' + ({} | randomNumber) }}</p>
```

Notice the usage of `({} | randomNumber)`. The input value is an empty object (`{}`), which doesn't change. However, since the pipe is impure, it generates a new random number on each change detection cycle.

# Debouncing

Debouncing is a technique used to delay or limit the number of times a function is executed in response to an event, particularly useful when dealing with user input events like typing in an input field. 

It ensures that a function is only called after a certain amount of time has passed since the last event, thereby reducing the frequency of function calls and improving performance.

1. **Install RxJS**:
Make sure you have `rxjs` installed in your Angular project. If not, you can install it using npm or yarn:

```bash
npm install rxjs
```

2. **Implement Debouncing**:
In your component, import `debounceTime` from `rxjs/operators`, and use it with an Observable to delay the execution of a function. For example, let's implement debouncing for a search input field:

```ts
import { Component, OnInit } from '@angular/core';
import { FormControl } from '@angular/forms';
import { debounceTime, distinctUntilChanged, switchMap } from 'rxjs/operators';
import { ApiService } from './api.service';

@Component({
  selector: 'app-search',
  templateUrl: './search.component.html',
  styleUrls: ['./search.component.css']
})
export class SearchComponent implements OnInit {

  searchControl: FormControl = new FormControl();

  constructor(private apiService: ApiService) { }

  ngOnInit(): void {
    this.searchControl.valueChanges
      .pipe(
        debounceTime(300), // Adjust the debounce time as needed
        distinctUntilChanged(), // Ensure the value has changed
        switchMap(value => this.apiService.search(value)) // Switch to the search API call
      )
      .subscribe(response => {
        // Handle API response
      });
  }
}


```

3. **HTML Template**:
In your HTML template, bind the `searchControl` to your input field using `ngModel` or reactive forms:

```html
<input type="text" [formControl]="searchControl" placeholder="Search...">
```

With this setup, the backend API will only be called after the user has stopped typing for the specified debounce time (300 milliseconds in this example), reducing unnecessary API requests and improving performance. Adjust the debounce time as needed based on your application's requirements.

# Set Css Class/Style based on expression

You can set CSS classes or inline styles dynamically based on expressions in Angular using property binding or ngClass/ngStyle directives. Here's how you can do it:

### Using Property Binding for CSS Classes:

You can use property binding (`[class.className]`) to conditionally apply CSS classes based on expressions.

```html
<div [class.error]="isError">Error message</div>
```

In your component class, you define the `isError` property based on some condition:
```ts
export class MyComponent {
  isError: boolean = true; // Or calculate based on some condition
}
```

### Using ngClass Directive:

You can also use the `ngClass` directive to conditionally apply CSS classes based on expressions.

```html
<div [ngClass]="{'error': isError, 'warning': isWarning}">Error or Warning message</div>
```

In your component class, you define properties like `isError` and `isWarning` based on your conditions.

### Using Inline Styles:

Similarly, you can use property binding (`[style.property]`) or the `ngStyle` directive to apply inline styles based on expressions.

```html
<div [style.color]="'red'">Red Text</div>
```

Or with ngStyle:

```html
<div [ngStyle]="{'color': isError ? 'red' : 'blue', 'font-weight': isBold ? 'bold' : 'normal'}">Dynamic Style</div>
```

In your component class, define properties like `isError` or `isBold` based on your conditions.

### Example:

Here's a complete example demonstrating how to apply CSS classes and inline styles dynamically:

```html
<!-- app.component.html -->
<div [class.error]="isError" [ngStyle]="{'color': isError ? 'red' : 'black', 'font-weight': isBold ? 'bold' : 'normal'}">
  {{ message }}
</div>
```

```ts
// app.component.ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  message = 'Hello, Angular!';
  isError = true;
  isBold = false;
}
```

In this example, the `isError` property determines whether the `error` CSS class is applied and whether the text color is set to red. The `isBold` property determines whether the text is bold or normal. You can adjust these properties based on your specific conditions.

# ngSwitchCase

`ngSwitchCase` is a directive in Angular that is used to conditionally display elements based on the value of an expression. It works in conjunction with `ngSwitch` directive to define a set of possible cases and then switch between them based on the value of the expression.

```html
<div [ngSwitch]="variable">
  <div *ngSwitchCase="'case1'">Content for Case 1</div>
  <div *ngSwitchCase="'case2'">Content for Case 2</div>
  <div *ngSwitchCase="'case3'">Content for Case 3</div>
  <div *ngSwitchDefault>Default Content</div>
</div>
```

```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-switch-example',
  templateUrl: './switch-example.component.html',
  styleUrls: ['./switch-example.component.css']
})
export class SwitchExampleComponent {
  variable: string = 'case2'; // Set the value of the variable here
}
```

- `ngSwitch`: This directive is applied to a parent element and takes an expression to match against.
- `ngSwitchCase`: This directive defines a case to match against the expression provided by `ngSwitch`. It evaluates the provided value and displays the content inside if the value matches.
- `ngSwitchDefault`: This directive is used to specify default content to be displayed if none of the cases match the expression provided by `ngSwitch`.

# Pagination and lazyloading using primeng

To implement pagination and lazy loading using PrimeNG, you can use the `p-table` component along with its features for pagination and lazy loading. Here's a step-by-step guide on how to do it:

1. **Install PrimeNG**:

```bash
npm install primeng
```

2. **Import PrimeNG Modules**:

Import the necessary PrimeNG modules in your Angular module file (e.g., `app.module.ts`):

```ts
import { TableModule } from 'primeng/table';
```

And add it to the imports array:

```ts
@NgModule({
  declarations: [/* your components */],
  imports: [
    /* other imports */
    TableModule
  ],
  providers: [],
  bootstrap: [/* your root component */]
})
export class AppModule { }
```

3. **Create a Data Service**:
   Create a service to fetch data from your backend API. This service will be used to load data lazily as the user navigates through pages.

4. **Implement Pagination and Lazy Loading**:
In your component HTML file (e.g., `my-component.component.html`), use the `p-table` component and configure it for pagination and lazy loading:

```html
<p-table [value]="yourData" [lazy]="true" [paginator]="true" [rows]="10" [totalRecords]="totalRecords" (onLazyLoad)="loadData($event)">
    <ng-template pTemplate="header">
        <!-- Table header -->
    </ng-template>
    <ng-template pTemplate="body" let-item>
        <!-- Table body -->
    </ng-template>
</p-table>
```

- `[value]`: Bind this to your data array.
- `[lazy]="true"`: Enable lazy loading.
- `[paginator]="true"`: Enable pagination.
- `[rows]="10"`: Number of rows per page.
- `[totalRecords]`: Total number of records. You need to update this value whenever the data changes.
- `(onLazyLoad)`: Event handler for lazy loading. Implement the `loadData` method in your component to load data lazily.

**Implement Lazy Loading Method**:
In your component TypeScript file (e.g., `my-component.component.ts`), implement the `loadData` method to fetch data lazily from your data service:

```ts
import { Component } from '@angular/core';
import { LazyLoadEvent } from 'primeng/api';
import { DataService } from './data.service';

@Component({
  selector: 'app-my-component',
  templateUrl: './my-component.component.html',
  styleUrls: ['./my-component.component.css']
})
export class MyComponent {

  yourData: any[] = [];
  totalRecords: number;

  constructor(private dataService: DataService) { }

  loadData(event: LazyLoadEvent): void {
    // Lazy load data from the service
    this.dataService.loadData(event.first, event.rows).subscribe(data => {
      this.yourData = data.results;
      this.totalRecords = data.totalRecords;
    });
  }
}
```

- Inject your data service (`DataService`) into the component.
- Implement the `loadData` method to load data lazily using the `LazyLoadEvent` parameters (e.g., `event.first`, `event.rows`).
- Update the `yourData` array and `totalRecords` value with the fetched data and total record count.

**Implement Data Service**:
Create a data service (e.g., `data.service.ts`) to fetch data from your backend API:

```ts
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { Observable } from 'rxjs';

@Injectable({
  providedIn: 'root'
})
export class DataService {

  constructor(private http: HttpClient) { }

  loadData(first: number, rows: number): Observable<any> {
    // Adjust your API URL and parameters
    const apiUrl = `your-api-url?start=${first}&limit=${rows}`;
    return this.http.get<any>(apiUrl);
  }
}
```

# Parent interacting with child via template reference

Interacting between parent and child components in Angular can be achieved using various techniques. One common method is using template reference variables to access child component properties and methods from the parent component's template.


1. **In the Parent Component Template**:
First, define a template reference variable in the parent component's template to reference the child component:

```html
<!-- parent.component.html -->
<app-child #childRef></app-child>
```

2. **In the Parent Component Class**:
Import `ViewChild` from `@angular/core` and use it to access the child component:

```ts
import { Component, ViewChild } from '@angular/core';
import { ChildComponent } from '../child/child.component';

@Component({
  selector: 'app-parent',
  templateUrl: './parent.component.html',
  styleUrls: ['./parent.component.css']
})
export class ParentComponent {
  @ViewChild('childRef', { static: true }) childComponent: ChildComponent;

  // Method in the parent component to interact with the child component
  interactWithChild(): void {
    // Call a method in the child component
    this.childComponent.childMethod();

    // Access a property in the child component
    console.log(this.childComponent.childProperty);
  }
}

```


3. **In the Child Component Class**:
Define methods and properties in the child component that you want to interact with from the parent component:

```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-child',
  templateUrl: './child.component.html',
  styleUrls: ['./child.component.css']
})
export class ChildComponent {
  childProperty: string = 'Child Property';

  childMethod(): void {
    console.log('Child Method Called');
  }
}
```

Now, you can call methods and access properties of the child component from the parent component using the `ViewChild` reference.

# Lifecycle Methods

In Angular 7, as in other versions, components have a lifecycle managed by Angular. These lifecycle events provide hooks into different stages of a component's lifecycle, allowing you to perform actions at specific times, such as initialization, change detection, and destruction. Here are the main lifecycle hooks in Angular components:

1. **ngOnChanges**: Called whenever one or more input properties of the component change. It's called before ngOnInit and before the first ngOnInit.
    
2. **ngOnInit**: Called once after the component is initialized. It's the perfect place to perform component initialization logic, such as fetching initial data.
    
3. **ngDoCheck**: Called during every change detection cycle, immediately after ngOnChanges and ngOnInit. It allows you to implement custom change detection logic.
    
4. **ngAfterContentInit**: Called once after Angular projects external content into the component's view. It's called after the component's content (e.g., projected content or child components' content) has been initialized.
    
5. **ngAfterContentChecked**: Called after Angular checks the content projected into the component. It's called after every check of the projected content.
    
6. **ngAfterViewInit**: Called once after the component's view (and its children) has been initialized. It's the perfect place to perform additional initialization logic that relies on the component's view.
    
7. **ngAfterViewChecked**: Called after Angular checks the component's view and its children. It's called after every check of the component's view.
    
8. **ngOnDestroy**: Called just before the component is destroyed. It's the perfect place to perform cleanup logic, such as unsubscribing from observables or releasing resources.

```ts
import { Component, OnInit, OnChanges, SimpleChanges, OnDestroy } from '@angular/core';

@Component({
  selector: 'app-lifecycle',
  template: `
    <p>{{ message }}</p>
  `
})
export class LifecycleComponent implements OnInit, OnChanges, OnDestroy {
  message: string = 'Hello, Angular!';
  counter: number = 0;

  constructor() {
    console.log('Constructor called');
  }

  ngOnInit(): void {
    console.log('ngOnInit called');
  }

  ngOnChanges(changes: SimpleChanges): void {
    console.log('ngOnChanges called', changes);
  }

  ngDoCheck(): void {
    console.log('ngDoCheck called');
  }

  ngAfterContentInit(): void {
    console.log('ngAfterContentInit called');
  }

  ngAfterContentChecked(): void {
    console.log('ngAfterContentChecked called');
  }

  ngAfterViewInit(): void {
    console.log('ngAfterViewInit called');
  }

  ngAfterViewChecked(): void {
    console.log('ngAfterViewChecked called');
  }

  ngOnDestroy(): void {
    console.log('ngOnDestroy called');
  }

  incrementCounter(): void {
    this.counter++;
  }
}

```

Here's a summary of the order in which these lifecycle methods are called:

```ts
ngOnChanges
ngOnInit
ngDoCheck
ngAfterContentInit
ngAfterContentChecked
ngAfterViewInit
ngAfterViewChecked
ngOnDestroy
```
---
# DAY 4

