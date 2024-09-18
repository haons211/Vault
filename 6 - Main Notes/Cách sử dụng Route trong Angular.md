
2024-09-17 16:50

Status:

Tags: [[Learning]] [[Front-end]] [[Angular]]

# Cách sử dụng Route trong Angular
haảo
cachách
   Step 1:     Create file routes.ts trong folder app Hảo
   Step 2:   Define path for route 
   ```typescript 
   const routeConfig: Routes = [
  {
    path: '',
    component: HomeComponent,
    title: 'Home page'
  },
  {
    path: 'details/:id',
    component: DetailsComponent,
    title: 'Home details'
  }
];

export default routeConfig;
```
   Step 3:     Open main.ts   . Import  #provideRouter , #routeConfig   để enable routing, and update bootstrap
Step 4. import #RouterModule vào app.component.ts
```typescript 
import { RouterModule } from '@angular/router';
```
   
```typescript
imports: [
  HomeComponent,
  RouterModule,
],
```

 Step 5: add routerlink và router-outlet 
 ```html
 template: `
  <main>
    <a [routerLink]="['/']">
      <header class="brand-name">
        <img class="brand-logo" src="/assets/logo.svg" alt="logo" aria-hidden="true">
      </header>
    </a>
    <section class="content">
      <router-outlet></router-outlet>
    </section>
  </main>
`,
```

# References


[[Routing trong Angular]]


