# Navigating the Angular2 Router
with Raju Gandhi
____
```
export interface Route {
  path?: string;
  pathMatch: string;
  matcher: UrlMatcher;
  component: Type<any>;
  redirectTo: string;
  //WHERE TO PLACE IN DOM
  outlet: string;
  //GUARDS
  canActivate?: any[];
  canActivateChild?: any[];
  canDeactivate?: any[];
  canLoad?: any[];
  //STATIC & DYNAMIC DATE
  data?: Data;
  resolve?: ResolveData;
  //CHILD ROUTES
  children?: Routes;
  loadChildren?: LoadChildren;
}
```

### Order Matters in Routes Array

```
export const routes: Routes = [
 {
   path: 'home',
   component: HomeComponent,
   data: { title: “Welcome!" }
 },
 //If this was first, you would inifinite loop to /home
 {
   path: ‘**', redirectTo: ‘/home', pathMatch: 'full'
 }
]
```

## Using Child Routes

```
{
  path: 'classes',
  component: ClassesComponent,
  data: { title: “Classes" },
  resolve: { classes: ClassesResolver },
  children: [
    {
      path: ':id',
      //Router will give :id to both children since no component was specified.
      //:id will be available via paramsMap.
      children: [
        {
          path: '',
          component: ClassComponent,
          resolve: { class: ‘classResolver' }
        },
        {
          path: '',
          component: DescriptionsComponent,
          resolve: {
            descriptions:‘descriptionsResolver'
          },
          outlet: 'descriptions'
        }
      ]
    }
  ]
}
```

Child Routes consume params in URL via their route paramsMap.

## Guards
Allow you to protect routes using an array of conditions.  All must pass or route will use redirectTo.

+ canLoad
+ canActivate
+ canActivateChild
+ canDeactivate

## Data
Static data that can be passed in at build time.

## Resolve
Data to be returned before component is initialized.

## Events

+ NavigationStart
+ NavigationEnd
+ NavigationCancel
+ NavigationError
+ RoutesRecognized
+ RouteConfigLoaded

```
//app.component.ts
export class AppComponent {
  loading = false;
  constructor(private router: Router) {
    router.events.subscribe((e: Event) => {
      this.navigationInterceptor(e);
    });
  }
  navigationInterceptor(event: Event): void {
    this.loading = (this.isStart(event) ? true : false);
  }
  isStart(event: Event): boolean {
    return event instanceof NavigationStart;
  }
  isEnd(event: Event): boolean {
    return (event instanceof NavigationEnd)
    || (event instanceof NavigationCancel)
    || (event instanceof NavigationError);
  }
}

//HTML
<div class="loading-overlay" *ngIf="loading">
 <md-progress-spinner mode="indeterminate"></md-progress-spinner>
</div>
```

## Debugging

```
RouterModule.forRoot(routes, { enableTracing: true });
```
