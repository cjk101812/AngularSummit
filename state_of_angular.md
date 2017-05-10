# State of Angular

Angular 5 coming out in September.

## Angular Versioning
+ Uses SEMVER

Angular 4 will contain breaking changes for those using Angular 2 (TypeScript versions, deprecation).
+ Will have recommended upgrade paths.
+ TypeScript is now accepted as an official language.

### The Mysterious Case of V3.
Angular core router was already on version 3 while other core dependencies were still on 2.x.x.  Decided to skip V3 to reduce confusion and get core dependencies on same versioning.

## Angular 4 Features

#### AOT Compilation (Ahead of Type)
+ Finds errors build time, rather than run-time.

#### FESM (Flattened ES Module)
+ Speeds up build.

#### Animations Removed from @core

#### Template Deprecated
+ Now use ng-template.

#### ngIf now supports else
```
<div ngIf='condition else false'></div>
```

#### HTTP Improvements

#### Form Validators
+ Email validation.

#### Use ParamMap for URL params.

#### ngPlural now baked in
+ ngPlural and pluralCase

#### Angular Universal
+ Server side rendering of templates.

#### Uses TypeScript 2.1/2.2
+ Lots of improvements.

#### Template SourceMaps

## V5 Features
Not many announcements.
