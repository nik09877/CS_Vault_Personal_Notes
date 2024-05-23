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
# Dynamic Component Loading

Dynamic component loading in Angular refers to the process of loading components at runtime, rather than at compile time. This capability allows you to create more flexible and customizable applications, where components can be loaded conditionally based on user interactions, data from APIs, or other runtime conditions.

### Why Dynamic Component Loading?

1. **Conditional Rendering:** You can load components based on certain conditions or user actions.
2. **Lazy Loading:** Components can be loaded on-demand, improving initial load time and overall performance.
3. **Runtime Configuration:** Components can be configured or customized dynamically based on runtime data.
4. **Plugin System:** Dynamic loading enables the creation of plugin systems where additional functionality can be added at runtime.

### How Dynamic Component Loading Works in Angular?

Angular provides several mechanisms for dynamically loading components:

1. **ComponentFactoryResolver:** This service allows you to get a reference to a component factory, which can then be used to create instances of the component dynamically.
    
2. **ViewContainerRef:** This represents a container where one or more components can be dynamically added or removed. It is typically used in conjunction with ComponentFactoryResolver.
    

### Example of Dynamic Component Loading in Angular 7:

Let's create a simple example where we have a button that, when clicked, dynamically loads one of two different components.

1. **Dynamic Component 1 (Component1Component):**

```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-component1',
  template: '<p>This is Component 1</p>'
})
export class Component1Component {}
```

2. **Dynamic Component 2 (Component2Component):**
```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-component2',
  template: '<p>This is Component 2</p>'
})
export class Component2Component {}
```

3. **Parent Component (AppComponent):**
```ts
import { Component, ComponentFactoryResolver, ViewChild, ViewContainerRef } from '@angular/core';
import { Component1Component } from './component1.component';
import { Component2Component } from './component2.component';

@Component({
  selector: 'app-root',
  template: `
    <button (click)="loadComponent1()">Load Component 1</button>
    <button (click)="loadComponent2()">Load Component 2</button>
    <div #dynamicComponentContainer></div>
  `
})
export class AppComponent {
  @ViewChild('dynamicComponentContainer', { read: ViewContainerRef }) container: ViewContainerRef;

  constructor(private resolver: ComponentFactoryResolver) {}

  loadComponent1() {
    this.container.clear();
    const factory = this.resolver.resolveComponentFactory(Component1Component);
    this.container.createComponent(factory);
  }

  loadComponent2() {
    this.container.clear();
    const factory = this.resolver.resolveComponentFactory(Component2Component);
    this.container.createComponent(factory);
  }
}
```

In this example:

- AppComponent has two buttons: one for loading Component1 and another for loading Component2.
- When a button is clicked, the corresponding component is dynamically loaded into the container using ComponentFactoryResolver.

# Authentication Guards

Authentication guards in Angular are used to control access to routes in an Angular application based on the authentication state of the user. They intercept navigation requests and either allow or deny access to certain routes based on predefined conditions. Angular provides several types of authentication guards:

1. **CanActivate:** This guard determines whether a route can be activated. It is typically used to prevent unauthorized users from accessing certain routes.
    
2. **CanActivateChild:** Similar to CanActivate, but it specifically guards child routes of a route.
    
3. **CanLoad:** This guard determines whether a module can be loaded lazily. It is useful for preventing the loading of feature modules by unauthorized users.
    
4. **CanDeactivate:** This guard is used to prevent navigation away from a route. It can be used to prompt the user for confirmation before leaving a route with unsaved changes.
    

### Example:

Let's create an example of an authentication guard using CanActivate to protect a route in an Angular application.

1. **Auth Service (auth.service.ts):**
```ts
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class AuthService {
  isLoggedIn = false;

  login() {
    this.isLoggedIn = true;
  }

  logout() {
    this.isLoggedIn = false;
  }

  isAuthenticated(): boolean {
    return this.isLoggedIn;
  }
}
```

2. **Authentication Guard (auth.guard.ts):**
```ts
import { Injectable } from '@angular/core';
import { CanActivate, ActivatedRouteSnapshot, RouterStateSnapshot, UrlTree, Router } from '@angular/router';
import { Observable } from 'rxjs';
import { AuthService } from './auth.service';

@Injectable({
  providedIn: 'root'
})
export class AuthGuard implements CanActivate {
  constructor(private authService: AuthService, private router: Router) {}

  canActivate(
    next: ActivatedRouteSnapshot,
    state: RouterStateSnapshot): Observable<boolean | UrlTree> | Promise<boolean | UrlTree> | boolean | UrlTree {
    if (this.authService.isAuthenticated()) {
      return true;
    } else {
      // Redirect to the login page if the user is not authenticated
      return this.router.parseUrl('/login');
    }
  }
}
```

3. **Route Configuration (app-routing.module.ts):**
```ts
import { NgModule } from '@angular/core';
import { Routes, RouterModule } from '@angular/router';
import { HomeComponent } from './home/home.component';
import { LoginComponent } from './login/login.component';
import { AuthGuard } from './auth.guard';

const routes: Routes = [
  { path: '', component: HomeComponent, canActivate: [AuthGuard] },
  { path: 'login', component: LoginComponent },
  { path: '**', redirectTo: '' } // Redirect to home if the route does not exist
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
```

In this example:

- The `AuthGuard` implements the `CanActivate` interface and checks if the user is authenticated using the `AuthService`.
- If the user is authenticated, the route is allowed to activate. Otherwise, the user is redirected to the login page.
- The `AuthGuard` is then added to the canActivate property of the route that needs to be protected (`HomeComponent` in this case).

This example demonstrates how to use the `CanActivate` guard to protect routes based on the authentication state of the user. Similar guards like `CanActivateChild`, `CanLoad`, and `CanDeactivate` can be implemented following similar patterns to meet different authentication requirements in an Angular application.

# Using Feature Modules

Feature modules in Angular are a way to organize an application into cohesive units of functionality, making it easier to manage, scale, and maintain. They group related components, directives, pipes, and services together, encapsulating them into reusable and independent units.

### Benefits of Feature Modules:

1. **Modularity:** Feature modules promote modularity by encapsulating related functionality into separate units. This makes it easier to understand, maintain, and reuse code.
    
2. **Scalability:** As an application grows, feature modules allow developers to organize and scale the application more effectively by breaking it down into smaller, manageable pieces.
    
3. **Reusability:** Feature modules can be reused across different parts of the application or even in different projects, promoting code reuse and reducing duplication.
    
4. **Lazy Loading:** Feature modules can be lazy-loaded, meaning they are only loaded when needed, which improves the initial loading time of the application and reduces the bundle size.
    

### Creating a Feature Module:

Let's create a simple feature module in an Angular application.

1. **Generate a Feature Module:**
```bash
ng generate module products
```
This command will generate a new module named `products` with its own folder and files.

2. **Define Components, Directives, Pipes, and Services:**

Within the `products` module, define components, directives, pipes, and services related to the functionality of managing products.

```bash
ng generate component products/product-list
ng generate component products/product-details
```

This command generates components for displaying a list of products and viewing product details within the `products` module.

3. **Import and Export Components, Directives, Pipes, and Services:**

In the `products.module.ts` file, import and declare the components, directives, pipes, and services that belong to the `products` module. Export any symbols that should be accessible to other modules.

```ts
import { NgModule } from '@angular/core';
import { CommonModule } from '@angular/common';
import { ProductListComponent } from './product-list/product-list.component';
import { ProductDetailsComponent } from './product-details/product-details.component';

@NgModule({
  declarations: [
    ProductListComponent,
    ProductDetailsComponent
  ],
  imports: [
    CommonModule
  ],
  exports: [
    ProductListComponent,
    ProductDetailsComponent
  ]
})
export class ProductsModule { }

```

4. **Import Feature Module:**

In the main application module (`app.module.ts`), import the `ProductsModule` to make its components, directives, pipes, and services available to the rest of the application.

```ts
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
import { ProductsModule } from './products/products.module';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    ProductsModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }

```

5. **Use Components, Directives, Pipes, and Services:**

Now, you can use the components, directives, pipes, and services defined in the `products` module in other parts of the application.

```ts
<!-- app.component.html -->
<h1>Product List</h1>
<app-product-list></app-product-list>

<h1>Product Details</h1>
<app-product-details></app-product-details>

```

# Validators:

In Angular, validators are used to validate user input in forms. Angular provides built-in validators like `required`, `minLength`, `maxLength`, etc. Additionally, you can create custom validators to suit specific validation requirements. Let's explore how to use both built-in and custom validators in Angular forms.

### Using Built-in Validators:

Angular provides a set of built-in validators that you can use out of the box. These validators are available as static methods in the `Validators` class.

1. **Import Validators:**
```ts
import { Validators } from '@angular/forms';
```

2. **Using Built-in Validators:**

Built-in validators are used by passing them as arguments to the `FormControl` constructor or to the `Validators.compose()` method.

```ts
import { Validators } from '@angular/forms';

// Example of using required validator
this.myForm = this.fb.group({
  username: ['', Validators.required], // Required validator
  email: ['', [Validators.required, Validators.email]], // Multiple validators
});

```

3. **Display Validation Errors in the Template:**

In the template, you can display validation errors using the `formControlName` directive along with Angular's `*ngIf` directive.

```html
<div *ngIf="myForm.get('username').errors?.required && myForm.get('username').touched">
  Username is required.
</div>
<div *ngIf="myForm.get('email').errors?.required && myForm.get('email').touched">
  Email is required.
</div>
<div *ngIf="myForm.get('email').errors?.email && myForm.get('email').touched">
  Please enter a valid email.
</div>

```

### Creating Custom Validators:

Custom validators are functions that take a `FormControl` object as input and return a validation error object if the validation fails, or `null` if the validation succeeds.

1. **Define a Custom Validator Function:**
```ts
import { AbstractControl, ValidatorFn } from '@angular/forms';

export function forbiddenNameValidator(forbiddenName: RegExp): ValidatorFn {
  return (control: AbstractControl): {[key: string]: any} | null => {
    const forbidden = forbiddenName.test(control.value);
    return forbidden ? {'forbiddenName': {value: control.value}} : null;
  };
}

```

2. **Using the Custom Validator:**

```ts
import { forbiddenNameValidator } from './forbidden-name-validator';

this.myForm = this.fb.group({
  username: ['', [Validators.required, forbiddenNameValidator(/admin/i)]],
});

```

3. **Display Validation Errors for Custom Validator:**
```html
<div *ngIf="myForm.get('username').errors?.required && myForm.get('username').touched">
  Username is required.
</div>
<div *ngIf="myForm.get('username').errors?.forbiddenName && myForm.get('username').touched">
  Username cannot contain 'admin'.
</div>

```

### Example:

Let's create a simple example to demonstrate the usage of both built-in and custom validators:

```ts
import { Component } from '@angular/core';
import { FormBuilder, FormGroup, Validators } from '@angular/forms';
import { forbiddenNameValidator } from './forbidden-name-validator';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  myForm: FormGroup;

  constructor(private fb: FormBuilder) {
    this.myForm = this.fb.group({
      username: ['', [Validators.required, forbiddenNameValidator(/admin/i)]],
      email: ['', [Validators.required, Validators.email]]
    });
  }
}

```

```html
<form [formGroup]="myForm">
  <div>
    <label for="username">Username:</label>
    <input type="text" id="username" formControlName="username">
    <div *ngIf="myForm.get('username').errors?.required && myForm.get('username').touched">
      Username is required.
    </div>
    <div *ngIf="myForm.get('username').errors?.forbiddenName && myForm.get('username').touched">
      Username cannot contain 'admin'.
    </div>
  </div>
  <div>
    <label for="email">Email:</label>
    <input type="email" id="email" formControlName="email">
    <div *ngIf="myForm.get('email').errors?.required && myForm.get('email').touched">
      Email is required.
    </div>
    <div *ngIf="myForm.get('email').errors?.email && myForm.get('email').touched">
      Please enter a valid email.
    </div>
  </div>
  <button type="submit" [disabled]="myForm.invalid">Submit</button>
</form>

```

In this example, we have created a form with two fields: username and email. We used both built-in validators (`required` and `email`) and a custom validator (`forbiddenNameValidator`) for the username field. We displayed validation errors in the template based on form control states.

---

# Rxjs library

1. **Observables**: Observables represent sequences of values that can be observed over time. They can emit multiple values asynchronously, and observers can subscribe to them to receive these values.

```ts
import { Observable } from 'rxjs';

const observable = new Observable<number>((observer) => {
  observer.next(1);
  observer.next(2);
  observer.next(3);
  setTimeout(() => observer.next(4), 1000);
});

const subscription = observable.subscribe({
  next: (value) => console.log(value),
  error: (err) => console.error('Error:', err),
  complete: () => console.log('Completed'),
});

// Output:
// 1
// 2
// 3
// (after 1 second) 4
// Completed

// Unsubscribe after 2 seconds
setTimeout(() => subscription.unsubscribe(), 2000);
```

2. **Operators**: Operators allow you to manipulate and transform observables, providing a wide range of functionalities.

```ts
import { from } from 'rxjs';
import { map, filter } from 'rxjs/operators';

from([1, 2, 3, 4, 5])
  .pipe(
    filter((x) => x % 2 === 0), // Filter even numbers
    map((x) => x * 10) // Multiply each value by 10
  )
  .subscribe((value) => console.log(value));

// Output:
// 20
// 40
// ```
```

3. **Subjects**: Subjects act as both an observable and an observer. They can multicast values to multiple subscribers.

```ts
import { Subject } from 'rxjs';

const subject = new Subject<number>();

subject.subscribe((value) => console.log('Observer 1:', value));
subject.subscribe((value) => console.log('Observer 2:', value));

subject.next(1);
subject.next(2);

// Output:
// Observer 1: 1
// Observer 2: 1
// Observer 1: 2
// Observer 2: 2

```

4. **Utility Functions**: RxJS includes utility functions for creating observables from various data sources (`of`, `from`, `interval`, `timer`, etc.) and for combining and manipulating observables (`merge`, `concat`, `forkJoin`, etc.).

```ts
import { of, interval } from 'rxjs';
import { merge } from 'rxjs/operators';

// Emit values from a list
of(1, 2, 3).subscribe((value) => console.log(value));

// Emit incremental values every second
interval(1000).subscribe((value) => console.log(value));

// Merge multiple observables into one
const observable1 = of('A', 'B', 'C');
const observable2 = interval(1000);
merge(observable1, observable2).subscribe((value) => console.log(value));
```

**mergeMap**:
- `mergeMap` flattens each observable emitted by the source observable into one observable, allowing concurrent requests.

```ts
import { fromEvent, interval } from 'rxjs';
import { mergeMap } from 'rxjs/operators';

const clicks = fromEvent(document, 'click');
const result = clicks.pipe(
  mergeMap((event) => interval(1000)) // Emit values every second for each click
);
result.subscribe((value) => console.log(value));

```

**switchMap**:
- `switchMap` cancels the previous inner observable when a new outer value is emitted, allowing only the latest observable to be subscribed to.

```ts
import { fromEvent, interval } from 'rxjs';
import { switchMap } from 'rxjs/operators';

const clicks = fromEvent(document, 'click');
const result = clicks.pipe(
  switchMap((event) => interval(1000)) // Emit values every second but only for the latest click
);
result.subscribe((value) => console.log(value));
```

- `concatMap` processes each value emitted by the source observable sequentially and waits for the inner observable to complete before emitting the next value.

```ts
import { fromEvent, interval } from 'rxjs';
import { concatMap } from 'rxjs/operators';

const clicks = fromEvent(document, 'click');
const result = clicks.pipe(
  concatMap((event) => interval(1000)) // Emit values every second but in a sequential order
);
result.subscribe((value) => console.log(value));
```

**combineLatest**:
- `combineLatest` combines multiple observables into one observable that emits an array of the latest values from each source observable whenever any source observable emits a new value.

```ts
import { combineLatest, interval } from 'rxjs';

const observable1 = interval(1000);
const observable2 = interval(2000);
const result = combineLatest([observable1, observable2]);
result.subscribe(([value1, value2]) => console.log(value1, value2));
```

**zip**:
- `zip` combines the values of multiple observables together, emitting arrays containing one value from each source observable.

```ts
import { zip, interval } from 'rxjs';

const observable1 = interval(1000);
const observable2 = interval(2000);
const result = zip(observable1, observable2);
result.subscribe(([value1, value2]) => console.log(value1, value2));

```

**Custom Operators**: Custom operators allow you to create your own operators by composing existing operators or implementing custom logic. This can be useful for encapsulating reusable logic or implementing specific behavior.

```ts
import { Observable, OperatorFunction } from 'rxjs';

function multiplyBy(factor: number): OperatorFunction<number, number> {
  return (source: Observable<number>) =>
    new Observable<number>((observer) => {
      const subscription = source.subscribe({
        next(value) {
          observer.next(value * factor);
        },
        error(error) {
          observer.error(error);
        },
        complete() {
          observer.complete();
        },
      });
      return () => subscription.unsubscribe();
    });
}

const observable = of(1, 2, 3).pipe(multiplyBy(2));
observable.subscribe((value) => console.log(value)); // Output: 2, 4, 6
```


# Multiple Instances of Service

If you need multiple instances of the same service in Angular, you can provide the service at the component level rather than at the root level. This way, each component can have its own instance of the service. Here's how you can achieve that:

**Create the Service:**
```ts
// example.service.ts
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'any' // This is to indicate that we won't provide it at the root level
})
export class ExampleService {
  constructor() { }

  // Your service methods go here
}

```

**Inject the Service in Components:**

In each component where you want a separate instance of the service, inject it into the constructor as usual.

```ts
// component1.component.ts
import { Component } from '@angular/core';
import { ExampleService } from './example.service';

@Component({
  selector: 'app-component1',
  templateUrl: './component1.component.html',
  styleUrls: ['./component1.component.css']
})
export class Component1Component {
  constructor(private exampleService: ExampleService) { }
}
```

```ts
// component2.component.ts
import { Component } from '@angular/core';
import { ExampleService } from './example.service';

@Component({
  selector: 'app-component2',
  templateUrl: './component2.component.html',
  styleUrls: ['./component2.component.css']
})
export class Component2Component {
  constructor(private exampleService: ExampleService) { }
}
```

1. **Using the Service:**
Now, each component will have its own instance of the `ExampleService`, and you can use it as needed within each component.
  
By providing the service with `providedIn: 'any'`, Angular creates a new instance of the service for each component that requests it. This gives you the flexibility to have multiple instances of the same service across different parts of your application.

# Server Side Rendering

Server-side rendering (SSR) in Angular 7 can be achieved using Angular Universal. Angular Universal is a technology that allows Angular applications to run on the server side. This can improve performance, enable better SEO, and provide a more consistent user experience, especially for users with slow internet connections or devices.

Here's a general overview of how to implement server-side rendering in Angular 7 with Angular Universal:

1. **Install Angular Universal:**
    
    First, you need to install Angular Universal and the necessary dependencies. You can use Angular CLI to set up Angular Universal in your existing Angular project:

```bash
ng add @nguniversal/express-engine
```

This command will add Angular Universal support to your project and set up the necessary files and dependencies.
    
2. **Build the Application for SSR:**
    
    Next, you need to build your Angular application specifically for server-side rendering. Angular Universal requires a separate build configuration for server-side rendering. You can build the application for SSR using the following command:

```bash
npm run build:ssr
```
 This command will create a server-side rendered version of your Angular application.
    
3. **Set Up Server-Side Code:**
    
    Angular Universal uses Node.js for server-side rendering. You need to set up a server-side code to serve your Angular application. This typically involves creating an Express.js server.
    
    Here's a basic example of setting up an Express server for serving Angular Universal applications:

```ts
// server.ts
import 'zone.js/dist/zone-node';
import * as express from 'express';
import { ngExpressEngine } from '@nguniversal/express-engine';
import { join } from 'path';

const app = express();

app.engine('html', ngExpressEngine({
  bootstrap: AppServerModule
}));

app.set('view engine', 'html');
app.set('views', join(__dirname, 'dist/browser'));

app.get('*.*', express.static(join(__dirname, 'dist/browser'), {
  maxAge: '1y'
}));

app.get('*', (req, res) => {
  res.render('index', { req });
});

app.listen(3000, () => {
  console.log(`Server running on http://localhost:3000`);
});

```

4. **Run the Server:**

Finally, you can start your server to serve the server-side rendered Angular application:

```bash
node server.js
```

This command will start the Express server, and your Angular application will be accessible at `http://localhost:3000`.

# User Input

User actions such as clicking a link, pushing a button, and entering text raise DOM events.

## Binding to user input events

To bind to a DOM event, surround the DOM event name in parentheses and assign a quoted [template statement](https://devdocs.io/angular~7/guide/template-syntax#template-statements) to it.

```html
<button (click)="onClickMe()">Click me!</button>
```

```ts
@Component({
  selector: 'app-click-me',
  template: `
    <button (click)="onClickMe()">Click me!</button>
    {{clickMessage}}`
})
export class ClickMeComponent {
  clickMessage = '';

  onClickMe() {
    this.clickMessage = 'You are my hero!';
  }
}
```

When the user clicks the button, Angular calls the `onClickMe` method from `ClickMeComponent`.

## Get user input from the $event object

DOM events carry a payload of information that may be useful to the component. This section shows how to bind to the `keyup` event of an input box to get the user's input after each keystroke.

The following code listens to the `keyup` event and passes the entire event payload (`$event`) to the component event handler.

```ts
template: `
  <input (keyup)="onKey($event)">
  <p>{{values}}</p>
`
```

When a user presses and releases a key, the `keyup` event occurs, and Angular provides a corresponding DOM event object in the `$event` variable which this code passes as a parameter to the component's `onKey()` method.

```ts
export class KeyUpComponent_v1 {
  values = '';

  onKey(event: any) { // without type info
    this.values += event.target.value + ' | ';
  }
}
```

The properties of an `$event` object vary depending on the type of DOM event. For example, a mouse event includes different information than an input box editing event.

All [standard DOM event objects](https://developer.mozilla.org/en-US/docs/Web/API/Event) have a [target](https://devdocs.io/angular~7/api/router/routerlinkwithhref#target) property, a reference to the element that raised the event. In this case, [target](https://devdocs.io/angular~7/api/router/routerlinkwithhref#target) refers to the [`<input>` element](https://developer.mozilla.org/en-US/docs/Web/API/HTMLInputElement) and `event.target.value` returns the current contents of that element.

After each call, the `onKey()` method appends the contents of the input box value to the list in the component's `values` property, followed by a separator character (|). The [interpolation](https://devdocs.io/angular~7/guide/template-syntax#interpolation) displays the accumulating input box changes from the `values` property.

## Get user input from a template reference variable
These variables provide direct access to an element from within the template. To declare a template reference variable, precede an identifier with a hash (or pound) character (#).

```ts
@Component({
  selector: 'app-loop-back',
  template: `
    <input #box (keyup)="0">
    <p>{{box.value}}</p>
  `
})
export class LoopbackComponent { }
```

The template reference variable named `box`, declared on the `<input>` element, refers to the `<input>` element itself. The code uses the `box` variable to get the input element's `value` and display it with interpolation between `<p>` tags.

It's easier to get to the input box with the template reference variable than to go through the `$event` object. Here's a rewrite of the previous `keyup` example that uses a template reference variable to get the user's input.

```ts
@Component({
  selector: 'app-key-up2',
  template: `
    <input #box (keyup)="onKey(box.value)">
    <p>{{values}}</p>
  `
})
export class KeyUpComponent_v2 {
  values = '';
  onKey(value: string) {
    this.values += value + ' | ';
  }
}
```

## Key event filtering (with `key.enter`)

The `(keyup)` event handler hears _every keystroke_. Sometimes only the _Enter_ key matters, because it signals that the user has finished typing. One way to reduce the noise would be to examine every `$event.keyCode` and take action only when the key is _Enter_.

There's an easier way: bind to Angular's `keyup.enter` pseudo-event. Then Angular calls the event handler only when the user presses _Enter_.

```ts
@Component({
  selector: 'app-key-up3',
  template: `
    <input #box (keyup.enter)="onEnter(box.value)">
    <p>{{value}}</p>
  `
})
export class KeyUpComponent_v3 {
  value = '';
  onEnter(value: string) { this.value = value; }
}
```

## On blur

In the previous example, the current state of the input box is lost if the user mouses away and clicks elsewhere on the page without first pressing _Enter_. The component's `value` property is updated only when the user presses _Enter_.

To fix this issue, listen to both the _Enter_ key and the _blur_ event.

```ts
@Component({
  selector: 'app-key-up4',
  template: `
    <input #box
      (keyup.enter)="update(box.value)"
      (blur)="update(box.value)">

    <p>{{value}}</p>
  `
})
export class KeyUpComponent_v4 {
  value = '';
  update(value: string) { this.value = value; }
}
```

# Hierarchical Dependency Injectors

The Angular dependency injection system is _hierarchical_. There is a tree of injectors that parallels an app's component tree. You can reconfigure the injectors at any level of that component tree.

You can configure providers for different injectors in the injector hierarchy. An internal platform-level injector is shared by all running apps. The `AppModule` injector is the root of an app-wide injector hierarchy, and within an NgModule, directive-level injectors follow the structure of the component hierarchy.

### @Injectable-level configuration

The @[Injectable](https://devdocs.io/angular~7/api/core/injectable)() decorator identifies every service class. The `providedIn` metadata option for a service class configures a specific injector (typically `root`) to use the decorated class as a provider of the service. When an injectable class provides its own service to the `root` injector, the service is available anywhere the class is imported.

```ts
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root',
})
export class HeroService {
  constructor() { }
}
```

### @NgModule-level injectors

You can configure a provider at the module level using the `providers` metadata option for a non-root NgModule, in order to limit the scope of the provider to that module. This is the equivalent of specifying the non-root module in the @[Injectable](https://devdocs.io/angular~7/api/core/injectable)() metadata, except that the service provided via `providers` is not tree-shakable.

You generally don't need to specify `AppModule` with `providedIn`, because the app's `root` injector is the `AppModule` injector. However, if you configure a app-wide provider in the @[NgModule](https://devdocs.io/angular~7/api/core/ngmodule)() metadata for `AppModule`, it overrides one configured for `root` in the @[Injectable](https://devdocs.io/angular~7/api/core/injectable)() metadata. You can do this to configure a non-default provider of a service that is shared with multiple apps.

Here is an example of the case where the component router configuration includes a non-default [location strategy](https://devdocs.io/angular~7/guide/router#location-strategy) by listing its provider in the `providers` list of the `AppModule`.

```ts
providers: [
  { provide: LocationStrategy, useClass: HashLocationStrategy }
]
```

### @Component-level injectors

Individual components within an NgModule have their own injectors. You can limit the scope of a provider to a component and its children by configuring the provider at the component level using the @[Component](https://devdocs.io/angular~7/api/core/component) metadata.

The following example is a revised `HeroesComponent` that specifies `HeroService` in its `providers` array. `HeroService` can provide heroes to instances of this component, or to any child component instances.

```ts
import { Component } from '@angular/core';

import { HeroService } from './hero.service';

@Component({
  selector: 'app-heroes',
  providers: [ HeroService ],
  template: `
    <h2>Heroes</h2>
    <app-hero-list></app-hero-list>
  `
})
export class HeroesComponent { }
```

# BootStrap 4

**1. Grid System:** Bootstrap's grid system allows you to create complex layouts by dividing the page into rows and columns. It is based on a 12-column layout system that scales dynamically based on screen size.

```html
<div class="container">
  <div class="row">
    <div class="col-md-6">Column 1</div>
    <div class="col-md-6">Column 2</div>
  </div>
</div>
```

**2. Navbar:** The Navbar component provides a responsive navigation bar that adapts to different screen sizes.

```html
<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
  <a class="navbar-brand" href="#">My Website</a>
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>
  <div class="collapse navbar-collapse" id="navbarSupportedContent">
    <ul class="navbar-nav ml-auto">
      <li class="nav-item">
        <a class="nav-link" href="#">Home</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">About</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">Contact</a>
      </li>
    </ul>
  </div>
</nav>
```

**3. Cards:** Cards are flexible and extensible content containers in Bootstrap 4, which allow you to display various types of content, such as images, text, and links, in a consistent manner.

```html
<div class="card">
  <img src="..." class="card-img-top" alt="...">
  <div class="card-body">
    <h5 class="card-title">Card title</h5>
    <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
    <a href="#" class="btn btn-primary">Go somewhere</a>
  </div>
</div>
```

**4. Forms:** Bootstrap provides a set of styles and classes to create attractive and responsive forms quickly.

```html
<form>
  <div class="form-group">
    <label for="exampleInputEmail1">Email address</label>
    <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email">
    <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
  </div>
  <div class="form-group">
    <label for="exampleInputPassword1">Password</label>
    <input type="password" class="form-control" id="exampleInputPassword1" placeholder="Password">
  </div>
  <div class="form-check">
    <input type="checkbox" class="form-check-input" id="exampleCheck1">
    <label class="form-check-label" for="exampleCheck1">Check me out</label>
  </div>
  <button type="submit" class="btn btn-primary">Submit</button>
</form>
```

**5. Buttons:** Bootstrap provides a variety of button styles and sizes to suit different needs.

```html
<button type="button" class="btn btn-primary">Primary</button>
<button type="button" class="btn btn-secondary">Secondary</button>
<button type="button" class="btn btn-success">Success</button>
<button type="button" class="btn btn-danger">Danger</button>
<button type="button" class="btn btn-warning">Warning</button>
<button type="button" class="btn btn-info">Info</button>
<button type="button" class="btn btn-light">Light</button>
<button type="button" class="btn btn-dark">Dark</button>
```

  
**6. Jumbotron:** The Jumbotron component is a lightweight, flexible component for showcasing key content on your site. It's often used for hero headers or call-to-action sections.

```html
<div class="jumbotron">
  <h1 class="display-4">Hello, world!</h1>
  <p class="lead">This is a simple hero unit, a simple jumbotron-style component for calling extra attention to featured content or information.</p>
  <hr class="my-4">
  <p>It uses utility classes for typography and spacing to space content out within the larger container.</p>
  <a class="btn btn-primary btn-lg" href="#" role="button">Learn more</a>
</div>
```

**7. Alerts:** Bootstrap provides styles for four different types of alerts: success, info, warning, and danger.

```html
<div class="alert alert-success" role="alert">
  This is a success alert—check it out!
</div>
<div class="alert alert-info" role="alert">
  This is a info alert—check it out!
</div>
<div class="alert alert-warning" role="alert">
  This is a warning alert—check it out!
</div>
<div class="alert alert-danger" role="alert">
  This is a danger alert—check it out!
</div>
```

**8. Carousel:** The Carousel component allows you to showcase multiple images or content in a slideshow format.

```html
<div id="carouselExampleIndicators" class="carousel slide" data-ride="carousel">
  <ol class="carousel-indicators">
    <li data-target="#carouselExampleIndicators" data-slide-to="0" class="active"></li>
    <li data-target="#carouselExampleIndicators" data-slide-to="1"></li>
    <li data-target="#carouselExampleIndicators" data-slide-to="2"></li>
  </ol>
  <div class="carousel-inner">
    <div class="carousel-item active">
      <img class="d-block w-100" src="..." alt="First slide">
    </div>
    <div class="carousel-item">
      <img class="d-block w-100" src="..." alt="Second slide">
    </div>
    <div class="carousel-item">
      <img class="d-block w-100" src="..." alt="Third slide">
    </div>
  </div>
  <a class="carousel-control-prev" href="#carouselExampleIndicators" role="button" data-slide="prev">
    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
    <span class="sr-only">Previous</span>
  </a>
  <a class="carousel-control-next" href="#carouselExampleIndicators" role="button" data-slide="next">
    <span class="carousel-control-next-icon" aria-hidden="true"></span>
    <span class="sr-only">Next</span>
  </a>
</div>
```

**9. Modals:** Modals are dialog boxes that overlay the main content of a page. They're useful for displaying additional content or interactive forms.

```html
<!-- Button trigger modal -->
<button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModal">
  Launch demo modal
</button>

<!-- Modal -->
<div class="modal fade" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">Modal title</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">
        ...
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary">Save changes</button>
      </div>
    </div>
  </div>
</div>

```

**10. Dropdowns:** Bootstrap provides styles for dropdown menus, which are useful for presenting a list of options to users.

```html
<div class="dropdown">
  <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
    Dropdown button
  </button>
  <div class="dropdown-menu" aria-labelledby="dropdownMenuButton">
    <a class="dropdown-item" href="#">Action</a>
    <a class="dropdown-item" href="#">Another action</a>
    <a class="dropdown-item" href="#">Something else here</a>
  </div>
</div>
```

---

# Differences between Angular.js and Angular

1. **Language and Architecture**:

- AngularJS was built using JavaScript and relied heavily on controllers, scope, and two-way data binding.
- Angular is built using TypeScript (a superset of JavaScript) and follows a more modular and component-based architecture.

>AngularJS (Angular 1.x) example:

```js
// app.js
var app = angular.module('myApp', []);

app.controller('MyController', function($scope) {
  $scope.message = 'Hello, World!';
});
```

```html
<!-- index.html -->
<div ng-app="myApp" ng-controller="MyController">
  {{ message }}
</div>
```

> Angular (Angular 2+) example:

```ts
// app.component.ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  template: '<h1>{{ message }}</h1>'
})
export class AppComponent {
  message = 'Hello, World!';
}
```

2. **Dependency Injection**:

- In AngularJS, dependency injection was achieved through string-based injection.
- In Angular, dependency injection is handled using a hierarchical injector system, which is more efficient and type-safe.

> AngularJS (Angular 1.x) example:

```js
app.controller('MyController', ['$scope', '$http', function($scope, $http) {
  // ...
}]);
```

> Angular (Angular 2+) example:

```ts
import { Component, Inject } from '@angular/core';
import { HttpClient } from '@angular/common/http';

@Component({
  // ...
})
export class MyComponent {
  constructor(@Inject(HttpClient) private http: HttpClient) {
    // ...
  }
}
```

3. **Rendering**:

- AngularJS used a dirty-checking mechanism to detect changes and update the DOM.
- Angular uses a more efficient change detection mechanism based on a unidirectional data flow.

4. **Modules**:

- In AngularJS, modules were used to organize code and dependencies.
- In Angular, modules are used for the same purpose, but they are defined using TypeScript decorators and have a more structured approach.

5. **Directives and Components**:

- AngularJS relied heavily on directives for creating reusable UI components.
- Angular introduced a more structured approach with components, which encapsulate templates, styles, and logic.

> AngularJS (Angular 1.x) directive example:

```js
app.directive('myDirective', function() {
  return {
    restrict: 'E',
    template: '<div>My Directive</div>'
  };
});
```

> Angular (Angular 2+) component example:

```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-my-component',
  template: '<div>My Component</div>'
})
export class MyComponent {}
```

6. **Template Syntax**:

- AngularJS used a more complex template syntax with features like `ng-repeat`, `ng-if`, `ng-model`, etc.
- Angular introduced a more straightforward and expressive template syntax, with structural directives like `*ngFor`, `*ngIf`, and property bindings like `[(ngModel)]`.

> AngularJS (Angular 1.x) template example:

```html
<div ng-repeat="item in items">{{ item }}</div>
<input ng-model="name" />
```

> Angular (Angular 2+) template example:

```html
<div *ngFor="let item of items">{{ item }}</div>
<input [(ngModel)]="name" />
```

7. **Routing**:

- In AngularJS, routing was handled by external libraries like `ngRoute` or `ui-router`.
- Angular has a built-in routing module (`@angular/router`) that provides advanced routing capabilities out of the box.

> AngularJS (Angular 1.x) routing example (with `ui-router`):

```js
app.config(function($stateProvider, $urlRouterProvider) {
  $urlRouterProvider.otherwise('/home');

  $stateProvider
    .state('home', {
      url: '/home',
      templateUrl: 'home.html'
    });
});
```

> Angular (Angular 2+) routing example:

```ts
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { HomeComponent } from './home.component';

const routes: Routes = [
  { path: 'home', component: HomeComponent },
  { path: '', redirectTo: '/home', pathMatch: 'full' }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule {}
```

8. **Angular CLI**:

- AngularJS did not have an official command-line interface (CLI) tool.
- Angular introduced the Angular CLI, which simplifies project setup, development, and build processes.

9. **Angular Universal**:

- Angular introduced Angular Universal, which allows for server-side rendering of Angular applications, improving initial load times and SEO.

10. **Backwards Compatibility**:

- AngularJS versions were largely backwards-compatible, at the cost of carrying technical debt.
- Angular introduced breaking changes with each major version, aiming for a more consistent and maintainable codebase, but requiring migration efforts between versions.

# Different Angular Versions and Features

## **Angular 2 (Released in September 2016)**:

**Component-based Architecture**: Angular 2 introduced a component-based architecture, where components are the building blocks of an application.

```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    <h1>{{ title }}</h1>
    <app-child [message]="message"></app-child>
  `
})
export class AppComponent {
  title = 'Hello, Angular 2!';
  message = 'This is a message from the parent component.';
}

@Component({
  selector: 'app-child',
  template: `<p>{{ message }}</p>`
})
export class ChildComponent {
  @Input() message: string;
}
```

**TypeScript and Decorators**: Angular 2 was written in TypeScript and made use of decorators for metadata annotations.

```ts
import { Injectable } from '@angular/core';

@Injectable()
export class MyService {
  // ...
}
```

## **Angular 4 (Released in March 2017)**:

Angular 4 was a minor release focused on bug fixes and performance improvements.

## **Angular 5 (Released in November 2017)**:

1. **Angular Universal (Server-side Rendering)**: Angular 5 introduced Angular Universal, which allows for server-side rendering of Angular applications.

```ts
// app.server.ts
import 'zone.js/dist/zone-node';
import 'reflect-metadata';
import { renderModuleFactory } from '@angular/platform-server';
import { AppServerModuleNgFactory } from './app.server.module.ngfactory';

renderModuleFactory(AppServerModuleNgFactory, {
  url: '/',
  document: '<app-root></app-root>'
}).then(html => {
  console.log(html);
});
```

2. **Progressive Web Apps (PWA) Support**: Angular 5 added support for building progressive web applications with service workers.

```ts
// app.module.ts
import { NgModule } from '@angular/core';
import { ServiceWorkerModule } from '@angular/service-worker';
import { environment } from '../environments/environment';

@NgModule({
  imports: [
    ServiceWorkerModule.register('ngsw-worker.js', { enabled: environment.production })
  ]
})
export class AppModule {}
```

## **Angular 6 (Released in May 2018)**:

1. **Angular Elements (Web Components)**: Angular 6 introduced Angular Elements, which allowed creating web components from Angular components.

```ts
import { Component, Input, ViewEncapsulation } from '@angular/core';

@Component({
  selector: 'app-hello-world',
  template: `<h1>Hello, {{ name }}!</h1>`,
  encapsulation: ViewEncapsulation.Native
})
export class HelloWorldComponent {
  @Input() name: string;
}
```

2. **Angular CLI Workspaces**: The Angular CLI introduced workspaces, allowing better management of multiple projects within a single workspace.

```bash
my-workspace/
  ├── package.json
  ├── angular.json
  ├── projects/
  │   ├── project1/
  │   └── project2/
  └── ...
```

## **Angular 7 (Released in October 2018)**:

1. **Virtual Scrolling**: Angular 7 introduced virtual scrolling, which improves performance by rendering only the visible portion of a large list.

```html
<cdk-virtual-scroll-viewport itemSize="50">
  <div *cdkVirtualFor="let item of items">{{ item }}</div>
</cdk-virtual-scroll-viewport>
```

2. **Drag and Drop**: Angular 7 added a built-in drag and drop module.

```html
<div cdkDrag>Drag me</div>
<div cdkDropList (cdkDropListDropped)="drop($event)">
  <div cdkDrag *ngFor="let item of items">{{ item }}</div>
</div>
```

## **Angular 8 (Released in May 2019)**:

1. **Differential Loading**: Angular 8 introduced differential loading, which allows serving different bundles for modern and legacy browsers.

```ts
// app.module.ts
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { AppComponent } from './app.component';

@NgModule({
  imports: [
    BrowserModule.withServerTransition({ appId: 'my-app' })
  ],
  declarations: [AppComponent],
  bootstrap: [AppComponent]
})
export class AppModule {}
```

2. **Web Workers**: Angular 8 added support for Web Workers, allowing offloading of compute-intensive tasks to a separate thread.

```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    <button (click)="startWorker()">Start Worker</button>
  `
})
export class AppComponent {
  worker: Worker;

  startWorker() {
    if (typeof Worker !== 'undefined') {
      this.worker = new Worker('./app.worker', { type: 'module' });
      this.worker.onmessage = ({ data }) => {
        console.log(`Worker result: ${data}`);
      };
      this.worker.postMessage('Hello, Worker!');
    } else {
      console.log('Web Workers are not supported in this environment.');
    }
  }
}
```

## **Angular 9 (Released in February 2020)**:

1. **Ivy Renderer**: Angular 9 introduced the Ivy renderer, which improved bundle sizes, performance, and type-checking.

```ts
import { Component, ViewEncapsulation } from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    <h1>Hello, Ivy!</h1>
    <app-child></app-child>
  `,
  encapsulation: ViewEncapsulation.ShadowDom
})
export class AppComponent {}
```

2. **Improved Dependency Injection**: Angular 9 improved the dependency injection system, making it more efficient and type-safe.

```ts
import { Component, Inject } from '@angular/core';
import { HttpClient } from '@angular/common/http';

@Component({
  // ...
})
export class MyComponent {
  constructor(@Inject(HttpClient) private http: HttpClient) {
    // ...
  }
}
```

## **Angular 10 (Released in June 2020)**:

Angular 10 focused on further improvements to the Ivy renderer and TypeScript support.

## **Angular 11 (Released in November 2020)**:

1. **Stricter TypeScript Settings**: Angular 11 introduced stricter TypeScript settings, improving type safety and null safety.

```ts
// tsconfig.json
{
  "compilerOptions": {
    "strict": true,
    "strictNullChecks": true,
    // ...
  }
}
```

2. **Language Service**: Angular 11 added a language service, providing better code completion, type-checking, and refactoring support in IDEs.

## **Angular 12 (Released in May 2021)**:

Angular 12 continued to improve TypeScript support and introduce stricter settings.


## **Angular 13 (Released in November 2021)**:

1. **Strict Templates**: Angular 13 introduced the `strictTemplates` flag, which enforces stricter type-checking for template expressions.

```ts
// tsconfig.json
{
  "compilerOptions": {
    "strict": true,
    "strictTemplates": true,
    // ...
  }
}
```

2. **Improved Ahead-of-Time (AoT) Compilation**: Angular 13 improved the performance and reliability of the AoT compilation process.

## **Angular 14 (Released in June 2022)**:

1. **Standalone Components**: Angular 14 introduced standalone components, allowing components to be used without an NgModule.

```ts
import { Component, standalone }
```

## Angular 15 (November 18, 2022)

### New Features:

- No specific features were listed for Angular 15.

## Angular 16 (May 3, 2023)

#### New Features:

1. **Partial Hydration for Angular Universal's Server-side Rendering:**
    - Enhanced SSR performance with partial hydration.
2. **Experimental Jest Support:**
    - Added support for the Jest testing framework.
3. **Esbuild-based Build System:**
    - Introduced an Esbuild-based build system for development servers.

```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-ssr',
  template: `<h1>Server-side Rendered Component</h1>`
})
export class SsrComponent {}

```


## Angular 17 (November 8, 2023)

#### New Features:

1. **Application Builder:**
    - Introduced a new application builder to streamline the build process.
2. **New Syntax for Control Flow:**
    - Enhanced control flow with a new syntax.
3. **Re-worked Learning and Documentation Website:**
    - Improved resources for learning and documentation.

> Code Example - New Syntax for Control Flow:

```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-example',
  template: `
    <ng-container *for="let item of items">
      <div>{{ item }}</div>
    </ng-container>
  `
})
export class ExampleComponent {
  items = ['Item 1', 'Item 2', 'Item 3'];
}

```