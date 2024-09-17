
2024-09-17 16:50

Status:

Tags: [[Learning]] [[Front-end]] [[Angular]]

# Cách sử dụng Route trong Angular


   Step 1:     Create file routes.ts trong folder app
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
   

# References


[[Routing trong Angular]]


