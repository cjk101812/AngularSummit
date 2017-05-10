# Web Apps with Angular
with Raju Gandhi
___

## Use AngularCLI
https://github.com/angular/angular-cli

Scaffold  | Usage
---       | ---
[Component](https://github.com/angular/angular-cli/wiki/generate-component) | `ng g component my-new-component`
[Directive](https://github.com/angular/angular-cli/wiki/generate-directive) | `ng g directive my-new-directive`
[Pipe](https://github.com/angular/angular-cli/wiki/generate-pipe)           | `ng g pipe my-new-pipe`
[Service](https://github.com/angular/angular-cli/wiki/generate-service)     | `ng g service my-new-service`
[Class](https://github.com/angular/angular-cli/wiki/generate-class)         | `ng g class my-new-class`
[Guard](https://github.com/angular/angular-cli/wiki/generate-guard)         | `ng g guard my-new-guard`
[Interface](https://github.com/angular/angular-cli/wiki/generate-interface) | `ng g interface my-new-interface`
[Enum](https://github.com/angular/angular-cli/wiki/generate-enum)           | `ng g enum my-new-enum`
[Module](https://github.com/angular/angular-cli/wiki/generate-module)       | `ng g module my-module`

Recommends VSCode
+ Written using TypeScript.
+ Great TypeScript support.

## Demo
Demo Code: https://gitlab.com/looselytyped/nfjs-angular-demo

```
git checkout d3ae6d44
```

#### Components

Uses the @angular/core "Component" import so that you can specify the Component annotation.

Components are identified by their selectors.

Example component.ts file:
```
//This is your import statement
import { Component } from "@angular/core";

//This is an annotation
@Component({
  selector: 'app-root'
  template: "path/to/html"
})

//This is your Class
export Class SampleComponent {
  //Component Code
}
```

#### Modules
```
//app.module.ts
import { Angular Modules } from 'paths';
import { Components } from 'path';

@ngModule({
  declarations: [

  ],
  //ANGULAR IMPORTS
  //Different from the imports above which are for TypeScript
  imports: [

  ],
  providers: [

  ],
  bootstrap: [
    AppComponent
  ]
})

export class AppModule { }
```

** Chrome Augury Plugin is a nice extension to view the Component tree. **
https://augury.angular.io/

BrowserModule allows Angular to render DOM from HTML.

```
import { BrowserModule } from '@angular/platform-browser';
```

You can export Components using an index.ts file within the Component directory. This allows you to rename, edit, etc. the Component without touching the ngModule.

```
//index.ts
export { SampleComponent } from './sample.component';

//app.module.ts ngModule referencing directory rather than file
import { SampleComponent } from './SampleComponent'
```

Component selectors can contain selectors like class, id, etc.  This is nice when trying to reuse selectors like <tr>.

```
//component.ts
@Component({
    selector: 'tr.class-name'
})

//HTML
<tr class="class-name"></tr>
```
