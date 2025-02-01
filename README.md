# Basics

## Components

Angular has it’s foundation on components, it’s their main feature. You can use Typescript, HTML and CSS to customize your components.

### Initialization

Exemple of a component:

```jsx
import {Component} from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    Hello
  `,
})
export class AppComponent {}

```

### Properties

You can also add properties to the class component, like a city:

```jsx
import {Component} from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    Hello {{ city }}, {{ 1 + 1 }}
  `,
})
export class AppComponent {
  city: String = 'San Francisco';
}

```

### Composing components

```jsx
import {Component} from '@angular/core';

@Component({
  selector: 'app-user',
  template: `
    Username: {{ username }}
  `,
})
export class UserComponent {
  username = 'youngTech';
}

@Component({
  selector: 'app-root',
  template: `<section><app-user /></section>`,
  imports: [UserComponent]
})
export class AppComponent {}

```

## Template Syntax

```jsx
@Component({
// ...
	template: `
      @if (isServerRunning) {
        <span>Yes, the server is running</span>
      } 
      @else {
        <span>No, the server is not running</span>
      }
  `,
 // ...
 })
 export class AppComponent {
  isLoggedIn = true;
  isServerRunning = true;
}
```

## Property binding

```jsx
import {Component} from '@angular/core';

@Component({
  selector: 'app-root',
  styleUrls: ['app.component.css'],
  template: `
    <div [contentEditable]="isEditable"></div>
  `,
})
export class AppComponent {
  isEditable = true;
}

```

## Event handling