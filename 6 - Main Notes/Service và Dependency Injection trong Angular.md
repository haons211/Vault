
2024-09-17 13:53

Status:

Tags: [[Front-end]] [[Angular]] [[Learning]]

# Service và Dependency Injection trong Angular
          Service là các class trong Angular , chứa logic hoặc dữ liệu mà nhiều component có thể sử dụng lại. 
          Tính năng : Tái sử dụng và có thể tiêm vào (Injection)

## Cách Dependency Injection hoạt động :

      Phải tiêm service vào component : tiêm bằng cách thông qua constructor của component.
      Angular sẽ inject service này khi component được khởi tạo
## Cách tạo service 

```bash
 ng generate service housing
```
          
```typescript 

// housing.service.ts
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root', // Service này có thể được sử dụng toàn ứng dụng
})
export class HousingService {
  constructor() { }

  getHousingLocations() {
    return [
      { id: 1, name: 'House A', location: 'City A' },
      { id: 2, name: 'House B', location: 'City B' },
      // Dữ liệu mẫu
    ];
  }
}

```

## Cách tiêm Service vào trong Component

```typescript
// app.component.ts
import { Component } from '@angular/core';
import { HousingService } from './housing.service'; // Import service

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  housingLocations: any[] = [];

  // Tiêm service vào thông qua constructor
  constructor(private housingService: HousingService) {}

  ngOnInit() {
    // Sử dụng service để lấy dữ liệu
    this.housingLocations = this.housingService.getHousingLocations();
  }
}


```
# References

[[Dependency Injection trong Java]]



