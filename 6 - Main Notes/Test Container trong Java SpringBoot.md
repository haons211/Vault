
2024-10-07 09:08

Status:

Tags:  [[Java]] [[Docker]] [[Learning]]
# Test Container trong Java SpringBoot

### Là gì ?
- Là một thư viện Java hỗ trợ kiểm thử tích hợp bằng cách tạo ra các container trong quá trình kiểm thử. Mục tiêu của nó là cung cấp các môi trường thử nghiệm gần giống với môi trường thực tế một cách dễ dàng và tự động .
### Nó sinh ra để giải quyết nỗi đau gì ?
- Trước khi có TestContainer . Người ta muốn test cái gì thông thường sẽ có 2 cách
  - Mocking : Sử dụng các mock service hoặc mock database. Khi test xong phải hồi lại mock.
  - Kiểm thử trên môi trường phụ thuộc thật sự . Có nghĩa là ví dụ muốn test elastic Search hay insert vào database. Người ta phải cung cấp tài nguyên thật. Gây ra lãng phí vô cùng
### Cách hoạt động của nó ?
- Tạo ra các container Docker khi bắt đầu test và tự động hủy chúng sau khi test hoàn tất
```java
import org.junit.jupiter.api.Test;
import org.springframework.boot.test.context.SpringBootTest;
import org.testcontainers.containers.PostgreSQLContainer;
import org.testcontainers.junit.jupiter.Container;
import org.testcontainers.junit.jupiter.Testcontainers;

@SpringBootTest
@Testcontainers
public class MyIntegrationTest {

    @Container
    public static PostgreSQLContainer<?> postgreSQLContainer = 
        new PostgreSQLContainer<>("postgres:13.3")
            .withDatabaseName("testdb")
            .withUsername("test")
            .withPassword("test");

    @Test
    void testDatabaseConnection() {
        // Test logic here, sử dụng postgreSQLContainer.getJdbcUrl() để kết nối tới cơ sở dữ liệu
    }
}

```

Trong ví dụ trên:

- **@Container**: Được sử dụng để đánh dấu container Docker cần được khởi chạy cho các bài test.
- Testcontainers tự động khởi tạo một container PostgreSQL, cung cấp một môi trường cơ sở dữ liệu mới và sau đó tự động dọn dẹp sau khi hoàn tất.
# References





