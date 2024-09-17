
2024-09-17 16:09

Status:

Tags: [[Front-end]] [[Angular]] [[Learning]]
# Routing trong Angular
```bash
ng new my-app --routing

```

      Routing trong Angular là khả năng điều hướng giữa các component.
      SPA (Single Page Application) , việc điều hướng khong tải lại toàn bộ trang mà chỉ thay đổi 1 phần của trang để hiển thị giao diện hoặc dữ liệu người dùng yêu cầu
## Angular Router 
     Angular Cli thường có tùy chọn để tự động tạo module routing .
     <router-outlet> là nơi hiển thị các component tương ứng với từng route

    Định nghĩa các Routes
```typescript 

// app-routing.module.ts
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { HomeComponent } from './home/home.component';
import { DetailsComponent } from './details/details.component';

const routes: Routes = [
  { path: '', component: HomeComponent },          // Route cho trang chủ
  { path: 'details', component: DetailsComponent } // Route cho trang chi tiết
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }

```


     Sử dụng <router-outlet> trong template
```html

<!-- app.component.html -->
<nav>
  <a routerLink="">Home</a> <!-- Liên kết đến route trang chủ -->
  <a routerLink="/details">Details</a> <!-- Liên kết đến route chi tiết -->
</nav>

<router-outlet></router-outlet> <!-- Component tương ứng với route sẽ hiển thị tại đây -->

```











# References





