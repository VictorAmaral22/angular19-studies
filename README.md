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

We use the “( )” to wrap the props on the HTML element, this way we can attach a certain function to it.

```jsx
import {Component} from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    <section (mouseover)="onMouseOver()">
      There's a secret message for you, hover to reveal:
      {{ message }}
    </section>
  `,
})
export class AppComponent {
  message = '';

  onMouseOver() {
    this.message = 'Way to go 🚀';
  }
}

```

## Input

Similar to props on React.

```jsx
import {Component, Input} from '@angular/core';

@Component({
  selector: 'app-user',
  template: `
    <p>The user's name is {{ name }}</p>
  `,
})
export class UserComponent {
  @Input() name = '';
}

```

```jsx
import {Component} from '@angular/core';
import {UserComponent} from './user.component';

@Component({
  selector: 'app-root',
  template: `
    <app-user name="Simran" />
  `,
  imports: [UserComponent],
})
export class AppComponent {}

```

## Output

It is used to trigger events to a parent component, similar to a event change on React.

```jsx
import {Component, Output, EventEmitter} from '@angular/core';

@Component({
  selector: 'app-child',
  styles: `.btn { padding: 5px; }`,
  template: `
    <button class="btn" (click)="addItem()">Add Item</button>
  `,
})
export class ChildComponent {
  @Output() addItemEvent = new EventEmitter<string>();

  addItem() {
    this.addItemEvent.emit('🐢');
  }
}

```

```jsx
import {Component} from '@angular/core';
import {ChildComponent} from './child.component';

@Component({
  selector: 'app-root',
  template: `
    <app-child (addItemEvent)="addItem($event)" />
    <p>🐢 all the way down {{ items.length }}</p>
  `,
  imports: [ChildComponent],
})
export class AppComponent {
  items = new Array();

  addItem(item: string) {
    this.items.push(item);
  }
}
```