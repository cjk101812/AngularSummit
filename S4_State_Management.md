# Advanced State Management
with Gerard Sans
___

### Versioning
+ Major releases March & Sept/Oct yearly.

### ngIf Changes from 2 to 4
```
// Angular 2
<div *ngIf="flightInfo">{{flightInfo.name}}</div>
<div *ngIf="!flightInfo">Loading...</div>

// Angular 4
<div *ngIf="flightInfo; else noInfo">{{flight.name}}</div>
<ng-template #noInfo>
 <div>Loading...</div>
</ng-template>
```

## Redux
#### Main Principles
+ Unidirectional data flow.
+ Single state (immutable).
+ New states are created without *side-effects*.

#### Reducers
+ Create new states in response to Actions applied to current state.
+ Reducers are *pure functions*.
+ Don't produce side-effects.

Example pure function:

```
// function foo(x) { return x+1; }
let foo = x => x+1;
// pure function
foo(1); // 2
foo(1); // 2
```

Example side-effects:
```
let flag = false;
let foo = x => {
  flag = !flag; // side effect
  return flag ? x+1: 0;
}
// not pure function
foo(1); // 2
foo(1); // 0
```

#### Middlewares

+ Sit between Actions and Reducers
+ Used for logging, storage, and async operations.
+ Composable

## ngrx

#### Store
+ Re-implementation of Redux on top
Angular and RxJS 5.
+ ngrx suite: store, effects, router, db

##### Observable
```
//Observable constructor
let simple$ = Rx.Observable.create(observer => {
  try {
    //pushing values
    observer.next(1);
    observer.next(2);
    observer.next(3);
    //complete stream
    observer.complete();
  }
  catch(e) {
    //error handling
    observer.error(e);
  }
});
```

##### Subscribe
```
/*
a$ ---1---2---3|
*/

let a$ = Rx.Observable.of(1,2,3);

let subscription = a$.subscribe({
  next: x => console.log(x),
  error: x => console.log('#'),
  complete: () => console.log('|')
});
```
Can also use unsubscribe to stop watching for changes.
