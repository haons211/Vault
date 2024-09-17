
2024-09-17 10:25

Status:

Tags: [[Front-end]] [[Learning]] [[Angular]]
# Các loại Component trong Angular

```typescript

import { Component } from '@angular/core';

// Định nghĩa Component
@Component({
  selector: 'app-home', // Thẻ HTML tùy chỉnh dùng để chèn component này vào template khác
  standalone: true,     // Chỉ rõ rằng component này không cần phải khai báo trong NgModule
  imports: [],          // Các phụ thuộc của component có thể được liệt kê ở đây
  template: `
    <div class="home-container">
      <h1>{{ title }}</h1>
      <p>Welcome to the Home Component!</p>
    </div>
  `,                    // Template HTML định nghĩa cấu trúc và bố cục của component
  styleUrls: ['./home.component.css'] // File CSS chứa kiểu dáng cho component
})
export class HomeComponent {
  title = 'Home Page';   // Logic của component (thuộc tính, phương thức, v.v.)
}

```

1. #selector :'app-home '  : Component sẽ được đại diện bởi thẻ <app-home> </app-home>
2. #standalone: true  . Có thể hoạt động độc lập
3. #import :[]     : trong ví dụ này không có sự phụ thuộc nào . Nhưng nếu sử dụng các form Angular chẳng hạn, bạn có thể liệt kê #FormsModule ở đây
4. #template Định nghĩa HTML cho một component .
5. #styleUrls: ['./home.component.css'] Các kiểu dáng được định nghĩa trong file CSS bên ngoài. Các kiểu dáng này chỉ áp dụng cho các phần tử HTML trong component này.
# References





