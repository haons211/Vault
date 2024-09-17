
2024-09-13 11:14

Status:

Tags:[[Learning]] , [[Front-end]]


# Definition of Component in React

#### 1. Definination
     Mỗi component trong React có thể là một phần giao diện đơn giản hoặc một phần cuả giao diện phức tạp hơn. Nó giúp chia nhỏ ứng dụng của các bạn thành các phần nhỏ hơn, dễ  quản lí và phát triển
     Các component nhận vào các props và có state để quản lí dữ liệu nội bộ . Khi component được render, nó trả về JSX (JS XML), mô tả giao diện người dùng nhìn thấy

#### 2. Các loại Component
##### 2.1 Functional Component ( Component Hàm)
      Là các component đơn giản được định nghĩa bằng một hàm.

```typescript
import React from 'react';

const Welcome: React.FC<{ name: string }> = ({ name }) => {
  return <h1>Hello, {name}!</h1>;
};

export default Welcome;

// Nhận vào props chứa name trả về JSX hiển thị tiêu đề "Hello, {name}"
```

##### 2.2 Class Component (Component lớp)
     Đây là kiểu component cũ hơn, vẫn được sử dụng nhưng không phổ biến bằng functional component.

```typescript 
import React, { Component } from 'react';

class Welcome extends Component<{ name: string }> {
  render() {
    return <h1>Hello, {this.props.name}!</h1>;
  }
}

export default Welcome;

```
# References

[[Tại sao component lại quan trọng]]
[Các loại Hooks thường gặp trong React]]

[[Props and State]]

