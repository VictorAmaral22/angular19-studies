# Angular v19

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