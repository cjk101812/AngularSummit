# Angular Styleguide
with Ben Ellingson
___

*John Papa's AngularJS and Angular Styleguides have both been officially adopted by the Angular team.*

## AngularJS Styleguide

```
// wrap components inside an Immediately Invoked Function Expression
;(function () {
  use strict';

  angular.module('myApp').controller('PersonController', PersonController);

  function PersonController() {

  }
})();
```
Note the preceding semi-colon above.  This can help prevent compilation errors.

## Angular Styleguide

Uses vocabulary to provide suggestions.

+ Do
+ Consider
+ Avoid

#### Use Consistent Naming

CLI helps enforce this by auto-generating files.

+ encourages readability and maintainability
+ CamelCase naming in components
+ name files by feature and type
+ separate file name parts with dots and dashes

#### Bootstrapping is done in main.ts
No business logic.

```
//main.ts
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';
import { enableProdMode } from '@angular/core';
import { environment } from './environments/environment';
import { AppModule } from './app/';

platformBrowserDynamic().bootstrapModule(AppModule);
```

#### Component Names

Use camel case and add a type suffix to Component names.

*File name should use feature.type.ts format*

#### Coding Conventions

+ Upper camel case class names
+ Lower camel case names for methods and properties

```
export class EmployeeListComponent {
  averageAge: number;

  fetchEmployees() {

  }
}
```

#### Application Structure

##### LIFT
+ L: Locating code is easy.
+ I: Identify code at a glance.
+ F: Flat structure.
+ T: Try to be DRY.

Keep a flat folder structure as long as possible.

Be DRY, but don't go nuts and sacrifice readability.

#### Core Feature Module

Do create a feature module named CoreModule in a core folder (e.g. app/core/core.module.ts defines CoreModule).

#### Components

+ Use kebab-case naming for component selectors.
+ Use HTML element selectors for components.
+ Extract templates and styles into their own files.

#### Member Sequencing

+ Place properties at the top followed by methods.
+ Place private members after public members, alphabetized.

```
export class EmployeeListComponent {

  message: string;
  title: string;
  private myVar: any;

  ngOnInit() {
    this.fetchEmployees()
  }

  private fetchEmployees() {
    // do fetch
  }

}
```

#### Serivces

+ Put business logic in Services.
+ Services are singletons.
+ Ideal for sharing stateful, in-memory data.

#### Data Services

+ Don't use http calls from within components.

#### Routing

Separate routing into a routing module. Focus only on routing.

```
import { AppRoutingModule } from './app-routing.module';

@NgModule({
  imports: [
  BrowserModule,
  FormsModule,
  AppRoutingModule
 ],
 declarations: [
  AppComponent,
  ProductComponent,
  ProductListComponent
 ],
 providers: [ ProductService ],
 bootstrap: [ AppComponent ]
})

export class AppModule { }
```

#### IDE/Text Editor

Optimize the tooling within your IDE/Editor to suite your needs.
