
2024-09-17 11:30

Status:

Tags: [[Front-end]] [[Learning]] [[Angular]]

# Định nghĩa Inputs trong Angular

     Inputs là một cơ chế cho phép các component chia sẻ dữ liệu với nhau . Cụ thể, Inputs cho phép truyền dữ liệu từ component cha đến component con.

      @Input() là 1 cơ chế được định nghĩa trong Angular .Thường được dùng trong component con . Khi một thuộc tính được gán @Input() , component cha có thể truyền giá trị cho thuộc tính đó thông qua binding dữ liệu trong template của component cha
      h


# Ví dụ
 ```typescript 
 // app.component.ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  // Dữ liệu để truyền đến component con
  house = {
    name: 'Beautiful House',
    address: '1234 Angular Lane, Ngonia'
  };
}


```


```html
<!-- app.component.html -->
<div>
  <h1>House Information</h1>
  <app-housing-location 
    [locationName]="house.name" 
    [locationAddress]="house.address">
  </app-housing-location>
</div>

```


```typescript 
// housing-location.component.ts
import { Component, Input } from '@angular/core';

@Component({
  selector: 'app-housing-location',
  templateUrl: './housing-location.component.html',
  styleUrls: ['./housing-location.component.css']
})
export class HousingLocationComponent {
  @Input() locationName: string = ''; // Thuộc tính để nhận tên địa điểm
  @Input() locationAddress: string = ''; // Thuộc tính để nhận địa chỉ địa điểm
}

```


```html
<!-- housing-location.component.html -->
<div class="location">
  <h2>{{ locationName }}</h2>
  <p>{{ locationAddress }}</p>
</div>

```







# References





