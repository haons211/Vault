
2024-09-13 14:04

Status:

Tags: [[Learning]] , [[Front-end]]
# Các loại Hooks thường gặp trong React

### 1. #useState

 Mục đích :  Quản lý trạng thái trong functional components. 
 
Khi sử dụng : Mỗi khi bạn cần lưu trữ và cập nhập trạng thái của component, chẳng hạn như số lượng, giá trị người dùng nhập vào, hoặc trạng thái của toggle (ví dụ : nốt chuyển trạng thái từ dark - light) .

Ví dụ 
```
import React, { useState } from 'react';

const Counter: React.FC = () => {
  const [count, setCount] = useState<number>(0); // Là React hook dùng để khai báo state.
    - `<number>`: Đây là cách TypeScript chỉ định kiểu dữ liệu cho          state. Ở đây, state `count` được khai báo là kiểu `number`
    - 'useState': trả về một mảng gồm 2 phần tử
          - count : Biến lưu giá trị của state
          - setCount: Hàm dùng để cập nhập giá trị của count khi cần
  const increment = (): void => setCount(count + 1);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
};

export default Counter;


```

### 2. #useEffect

      Mục đích : Thực hiện side effects trong component , như gọi API, thiết lập subscription , hoặc thay đổi DOM sau khi render.
      Khi sử dụng : Khi bạn cần thực hiện các tác vụ bên ngoài React , như fetch dữ liệu từ server, cập nhập tiêu đề trang, hoặc thiết lập timers.

Ví dụ 
```typescript
import React, { useState, useEffect } from 'react';

interface Data {
 id: number;
 name : string;
}

const DataFetcher: React.FC = () => {
const [data, setData] = useState<Data | null>(null); 

     useEffect(() => { 
     fetch('https://api.example.com/data') 
     .then(response => response.json()) 
     .then(data => setData(data)); }, []); 
     return ( 
     <div> 
     <p>Data: {data ? JSON.stringify(data) : 'Loading...'}</p> 
     </div> ); };
     export default DataFetcher;
```

### 3. #useContext 

    Mục đích: Dùng để chia sẻ dữ liệu giữa các component mà không cần truyển props qua nhiêu lớp. 'useContext' giúp truy cập giá trị từ context được cung cấp bởi 'React.createContext'.
     Khi sử dụng  : Bàn cần truyền dữ liệu họăc hàm từ component cha đến component con mà không cần phải truyền qua nhiều cấp
Ví dụ: 
 ```typescript
import React, { createContext, useContext } from 'react';

// Tạo một context để lưu trữ thông tin theme . // đang thực hiện
// ở 1 component khác
const ThemeContext = createContext<string>('light');

const ThemedComponent: React.FC = () => {
  // Truy cập giá trị của theme kia thông qua useContext
  const theme = useContext(ThemeContext);

  return <div>The current theme is {theme}</div>;
};

const App: React.FC = () => (
  // Cung cấp giá trị 'dark' cho tất cả các component con qua ThemeContext.Provider
  <ThemeContext.Provider value="dark">
    <ThemedComponent />
  </ThemeContext.Provider>
);

export default App;

```


### 4. #useRef

     - **Mục đích**: Tạo một tham chiếu có thể được sử dụng để truy cập trực tiếp các DOM element hoặc để lưu trữ giá trị không kích hoạt re-render khi thay đổi.
    
    - **Khi sử dụng**: Khi bạn cần truy cập DOM element như `input`, hoặc lưu trữ giá trị nào đó qua các lần render mà không cần cập nhật giao diện

```typescript
import React, { useRef } from 'react';

const FocusInput: React.FC = () => {
  // Tạo ref cho phần tử input
  const inputRef = useRef<HTMLInputElement>(null);

  const focusInput = (): void => {
    // focus vào input nếu ref hiện tại tồn tại
    if (inputRef.current) {
      inputRef.current.focus();
    }
  };

  return (
    <div>
      <input ref={inputRef} type="text" />
      <button onClick={focusInput}>Focus Input</button>
    </div>
  );
};

export default FocusInput;

```


### 5. #useCallback

     -- **Mục đích**: Dùng để ghi nhớ (memoize) một hàm, giúp tối ưu hóa hiệu suất bằng cách tránh tạo ra các hàm mới không cần thiết mỗi lần component re-render.
    
    - **Khi sử dụng**: Khi bạn có các hàm phụ thuộc vào props hoặc state và bạn muốn tối ưu hóa hiệu suất, đặc biệt khi truyền các hàm này xuống các component con

```typescript
import React, { useState, useCallback } from 'react';

const Button: React.FC<{ onClick: () => void }> = React.memo(({ onClick }) => {
  console.log('Button rendered');
  return <button onClick={onClick}>Click me</button>;
});

const ParentComponent: React.FC = () => {
  const [count, setCount] = useState<number>(0);

  // useCallback sẽ ghi nhớ hàm 'handleClick', chỉ tạo lại khi dependencies thay đổi
  const handleClick = useCallback(() => {
    console.log('Button clicked');
  }, []); // Hàm chỉ được tạo một lần

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <Button onClick={handleClick} />
    </div>
  );
};

export default ParentComponent;

```



### 5. #useMemo

    **Mục đích**: Ghi nhớ (memoize) một giá trị tính toán phức tạp, chỉ tính toán lại khi các dependencies thay đổi, giúp tối ưu hóa hiệu suất của các tác vụ tính toán nặng.
    
    - **Khi sử dụng**: Khi bạn có một giá trị phức tạp cần tính toán và không muốn nó bị tính toán lại mỗi khi component re-render.

```typescript
import React, { useState, useMemo } from 'react';

const ExpensiveComponent: React.FC<{ a: number; b: number }> = ({ a, b }) => {
  // Hàm tính toán phức tạp
  const computeExpensiveValue = (a: number, b: number): number => {
    console.log('Computing expensive value');
    return a + b;
  };

  // useMemo chỉ tính toán lại khi 'a' hoặc 'b' thay đổi
  const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);

  return <div>Computed Value: {memoizedValue}</div>;
};

const App: React.FC = () => {
  const [a, setA] = useState<number>(1);
  const [b, setB] = useState<number>(2);

  return (
    <div>
      <ExpensiveComponent a={a} b={b} />
      <button onClick={() => setA(a + 1)}>Change A</button>
      <button onClick={() => setB(b + 1)}>Change B</button>
    </div>
  );
};

export default App;






