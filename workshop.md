# Introduction to Angular with Typescript

## Typescript

### Classes
```
export class Shape {
 name: string;
 sides: number;
 constructor(name: string, sides: number) {
   this.name = name;
   this.sides = sides;
 }
 describe() {
   console.log(`A ${this.name} has ${this.sides} sides`);
 }
}
```

##### Inheritance
```
export class Square extends Shape {
  constructor() {
    super('square', 4)
  }
}
let square = new Square();
square.describe();
// A square has 4 sides
```

### Types
```
export class Author {
 id: number;
 name: string;
 age: number;
 isAlive: boolean;

 books: Array<Book>;

 articles: Array<any>;
}
```

### Methods (Functions)

Functions within a class.

##### let
Strict scope not referenced outside function.

### Import
Import classes by referencing file path.

`import {Square} from './shape'`

### Fat Arrow Functions
```
let myFunction = (message) => {
  console.log(message)
}
```

## Angular CLI

Generates source files for project.
+ index.html
+ main.ts
+ app.module.ts
+ app.component.ts
+ app.component.html

### Components


### Templates

Sass built in.  Just update file extensions.

#### Syntax
##### ngFor
Looping through array.

##### ngIf
Rendering within template.

```
<ul *ngIf="enabled">
  <li *ngFor="let x of myArray">{{x}}</li>
</ul>
```

##### (Events)
```
// my-component.html
<button (click)="handleClick('Hello From Child Template')">Ok</button>

// my.component.ts
export class MyComponent {
 handleClick(value) {
 alert('Handle Click: ' + value);
 }
}
```

##### [Attributes]
```
<button [disabled]="disabled">OK</button>

// my.component.ts
export class MyComponent {
 disabled = true;
 checked = true;
}
```

##### [Inputs]
Same syntax as attributes, but on a component.
```
<child-component [item]="item"></child-component>

export class MyComponent {
 item = { id: 1, name: 'My Item' };
}
export class MyChildComponent {
 @Input() item;
}
```

### Angular Forms
```
<form #f="ngForm" (ngSubmit)="addProduct(f.value)">
 <input type="text" name="name" ngModel required/>
 <input type="text" name="price" ngModel required/>
 <button [disabled]="!f.valid">Add</button>
</form>
```

### Services

#### Observables
Used for async operations like http requests.

Replace the promises API.

### Routing
Manages state transitions between views in your SPA.

ANGULAR 3 VERSION SKIP WAS TO ELIMINATE CONFUSION WITH THE VERSION 3 ROUTER!!!!
