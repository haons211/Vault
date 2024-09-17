
2024-09-13 15:58

Status:

Tags: [[Front-end]], [[Learning]]

# Tại sao component lại quan trọng

React sử dụng các component để tái sử dụng các phần tử giao diện. Thay vì viết mã dài và phức tạp cho toàn bộ ứng dụng, bạn có thể chia giao diện thành các component nhỏ, dễ quản lý và tái sử dụng.

```typescript 
const Button: React.FC<{ label: string }> = ({ label }) => {
  return <button>{label}</button>;
};

// Sử dụng Button ở nhiều nơi trong ứng dụng
<Button label="Submit" />;
<Button label="Cancel" />;

```
# References





