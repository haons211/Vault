

### *1. Spring Cloud Gateway**


#### **Routing:**

- **Keywords:**
    - Spring Cloud Gateway Routing
    - Spring Gateway Path Predicate
    - application.yml route configuration
    - Route Definition Locator
    -------------------------------
    Bạn có thể đĩnh nghĩa route trong application.yml để chỉ định yêu cầu API đi đến dịnh vụ tương ứng.  Chúng ta có  2 file application.yml đại diện cho 2 service `user-service` và `gateway-service`
    ```yaml
spring:  
  application:  
    name: user-service
```
     explain : Khai báo tên ứng dụng là user-service
    
    ```yaml 
    spring:  
  application:  
    name: gateway-service  
  
  cloud:  
    gateway:  
      routes:  
        - id: user-service  
          uri: lb://user-service  
          predicates:  
            - Path=/users/**

```
   Giải thích file yml :  
   + ```user_service``` : Identifier cho route. Bạn có thể đổi thành tên những gì bạn muốn . thông thường sẽ đặ theo tên service
	   + ```uri: lb://user-service``` :  lb là viết tắt của `Load Balancing` . Thay vì đưa một địa chỉ cụ thể  thì Gateway sẽ sử dụng một cân bằng tải để phân phối yêu cầu bản sao của dịch vụ người dùng (ví dụ user-service chạy trên các máy chúng khác nhau ), trong bài hiện tại đang chỉ có duy nhất 1 service chạy
	   + `predicates: - Path=/users/**` : định nghĩa rằng bất kỳ yêu cầu nào có đường dẫn bắt đầu bằn `/users` sẽ được chuyển đến `user-service` thông qua cân bằng tải. Ví dụ :
	     - `/users/123` sẽ chuyển đến `user-service`
	     - `users/profile` cũng sẽ chuyển đến user-service
	   

#### **Filters:**

- **Keywords:**
    - Spring Cloud Gateway Filters
    - Pre-filters and Post-filters
    - GlobalFilter vs GatewayFilter
    - AddRequestHeader filter
    - ModifyResponseBody filter

#### **Integration with Spring Security:**

- **Keywords:**
    - Spring Gateway with OAuth2
    - JWT in Spring Cloud Gateway
    - SecurityWebFilterChain
    - OAuth2ResourceServer
    - Token Relay in Gateway

#### **Load Balancing:**

- **Keywords:**
    - Spring Cloud Gateway Load Balancing
    - Spring Cloud LoadBalancer
    - Netflix Ribbon vs Spring LoadBalancer
    - Service Discovery with LoadBalancer
    - Gateway and Eureka integration

---

### **2. Eureka từ Spring Cloud Netflix**

#### **Service Registration and Discovery:**

- **Keywords:**
    - Spring Cloud Eureka Client
    - @EnableEurekaClient
    - Eureka Server and Client Configuration
    - Spring Boot Service Discovery

#### **Health Check:**

- **Keywords:**
    - Eureka Health Check
    - Spring Boot Actuator with Eureka
    - Eureka Health Status
    - application.yml health check configuration

#### **Service Instances and Load Balancing:**

- **Keywords:**
    - Eureka with multiple service instances
    - Service instance discovery with Eureka
    - Eureka Load Balancing
    - Ribbon with Eureka
    - Spring Cloud LoadBalancer Eureka integration

---

### **3. Spring Security với JWT và OAuth2**

#### **JWT Basics:**

- **Keywords:**
    - Spring Security JWT
    - JWT Header Payload Signature
    - Spring Boot JWT Authentication
    - Stateless Authentication with JWT

#### **OAuth2 Authorization Flows:**

- **Keywords:**
    - OAuth2 Client Credentials Flow
    - OAuth2 Resource Owner Password Flow
    - OAuth2 Authorization Code Flow
    - OAuth2 Access Tokens and Refresh Tokens

#### **Configuring Security Filters:**

- **Keywords:**
    - Spring Security Filter Chain
    - WebSecurityConfigurerAdapter JWT
    - OAuth2ResourceServer with JWT
    - Securing REST APIs with Spring Security and JWT
    - Role-Based Access Control (RBAC) in Spring Security


## Keycloak, Oauth2,JWT
Giải thích Keycloak, JWT, và OAuth2 có thể được thực hiện qua cách đơn giản hóa và sử dụng ví dụ thực tế. Dưới đây là cách tiếp cận mà bạn có thể sử dụng:

### 1. Khái Niệm Cơ Bản

**Keycloak**: Là một giải pháp quản lý danh tính và quyền truy cập (Identity and Access Management - IAM) mã nguồn mở. Keycloak cho phép bạn thêm đăng nhập một lần (Single Sign-On - SSO), quản lý người dùng, và phân quyền cho các ứng dụng của bạn mà không cần phải viết mã từ đầu.

**OAuth2**: Là một giao thức ủy quyền (authorization protocol) cho phép ứng dụng của bạn truy cập vào thông tin từ một dịch vụ khác mà không cần tiết lộ mật khẩu của người dùng. Thay vào đó, OAuth2 sử dụng các "token" để ủy quyền.

**JWT (JSON Web Token)**: Là một định dạng token được sử dụng để truyền thông tin giữa các bên dưới dạng một đối tượng JSON. JWT thường được sử dụng trong OAuth2 để xác thực và ủy quyền.

### 2. Mô Hình Hóa Ví Dụ Thực Tế

#### Tình Huống:

Giả sử bạn có một ứng dụng bán hàng trực tuyến có nhiều dịch vụ (microservices) như:

- **User Service**: Quản lý thông tin người dùng.
- **Product Service**: Quản lý sản phẩm.
- **Order Service**: Quản lý đơn hàng.

Khi người dùng muốn đăng nhập vào ứng dụng, bạn muốn họ có thể sử dụng tài khoản Google của mình để đăng nhập, mà không cần phải tạo tài khoản mới.

#### Quy Trình Đăng Nhập:

1. **Người dùng truy cập vào ứng dụng**.
2. **Người dùng nhấn nút "Đăng nhập với Google"**.
3. **Ứng dụng sẽ chuyển hướng đến Keycloak**, nơi người dùng được yêu cầu xác thực thông qua tài khoản Google của họ.
4. Sau khi người dùng đăng nhập thành công, Keycloak sẽ:
    - Tạo một **JWT** cho người dùng, chứa thông tin như ID người dùng, tên, và quyền hạn.
    - Gửi token này về lại ứng dụng.
5. **Ứng dụng sẽ nhận được JWT** và lưu lại (ví dụ trong bộ nhớ của trình duyệt).
6. Khi người dùng thực hiện các hành động trong ứng dụng (như xem sản phẩm, đặt hàng), ứng dụng sẽ gửi **JWT** này đến các dịch vụ khác (User Service, Product Service, Order Service) để xác thực và ủy quyền.
7. **Mỗi dịch vụ** sẽ kiểm tra token để đảm bảo rằng người dùng có quyền truy cập vào tài nguyên mà họ yêu cầu.

### 3. Mối Quan Hệ Giữa Keycloak, OAuth2, và JWT

- **Keycloak** sử dụng **OAuth2** làm giao thức để quản lý ủy quyền và xác thực.
- Khi người dùng đăng nhập, Keycloak phát hành một **JWT**, chứa thông tin xác thực và quyền hạn của người dùng.
- **JWT** được sử dụng trong các yêu cầu tiếp theo giữa ứng dụng và các dịch vụ khác để xác thực người dùng mà không cần phải gửi mật khẩu của họ mỗi lần.

### 4. Tóm Tắt

- **Keycloak**: Quản lý danh tính và quyền truy cập, cho phép xác thực và ủy quyền.
- **OAuth2**: Giao thức để ủy quyền cho ứng dụng truy cập vào thông tin của người dùng.
- **JWT**: Token xác thực, chứa thông tin về người dùng và quyền hạn.

### 5. Kết Luận

Việc sử dụng Keycloak trong ứng dụng của bạn giúp đơn giản hóa quy trình quản lý người dùng và bảo mật, đồng thời tăng trải nghiệm người dùng bằng cách cho phép họ đăng nhập một cách dễ dàng thông qua các tài khoản hiện có.
Vậy Keycloak sẽ là nơi tạo token, còn Oauth2 sử dụng token

###### ChatGPT đã nói:

ChatGPT

Đúng rồi! Keycloak sẽ là nơi tạo và quản lý token, trong khi OAuth2 là giao thức giúp quản lý quá trình ủy quyền và xác thực dựa trên token đó. Dưới đây là tóm tắt chi tiết hơn về vai trò của từng thành phần trong quy trình này:

### 1. **Vai Trò của Keycloak**

- **Xác thực người dùng**: Keycloak quản lý quá trình xác thực người dùng, có thể thông qua tài khoản trực tiếp, tài khoản mạng xã hội (như Google), hoặc tài khoản doanh nghiệp.
- **Phát hành token**: Khi người dùng đăng nhập thành công, Keycloak sẽ phát hành một token (thường là JWT) cho người dùng đó. Token này chứa thông tin xác thực (như ID người dùng, quyền truy cập) và có thể được sử dụng để xác thực trong các yêu cầu tiếp theo.
- **Quản lý phiên**: Keycloak có khả năng quản lý phiên làm việc của người dùng, cho phép người dùng đăng xuất, làm mới token, hoặc kiểm soát quyền truy cập.

### 2. **Vai Trò của OAuth2**

- **Quy trình ủy quyền**: OAuth2 định nghĩa cách mà các ứng dụng có thể yêu cầu quyền truy cập đến thông tin của người dùng từ một dịch vụ khác mà không cần biết mật khẩu của họ. Trong trường hợp của Keycloak, ứng dụng của bạn sẽ thực hiện quy trình OAuth2 để ủy quyền cho người dùng.
- **Sử dụng token**: Khi ứng dụng nhận được token từ Keycloak, nó sẽ sử dụng token đó trong các yêu cầu đến các dịch vụ khác (như User Service, Product Service). Token này chứng minh rằng người dùng đã được xác thực và có quyền truy cập vào tài nguyên mà họ yêu cầu.
- **Bảo vệ tài nguyên**: Các dịch vụ sẽ kiểm tra token để đảm bảo rằng nó hợp lệ và chưa hết hạn trước khi cho phép truy cập vào tài nguyên của chúng.

### 3. **Quy Trình Tóm Tắt**

1. **Người dùng đăng nhập**: Người dùng gửi yêu cầu đăng nhập (qua Keycloak).
2. **Keycloak xác thực**: Keycloak xác thực thông tin đăng nhập và phát hành token (JWT) cho người dùng.
3. **Ứng dụng sử dụng token**: Ứng dụng nhận được token và lưu nó lại để sử dụng sau này.
4. **Gửi yêu cầu đến các dịch vụ khác**: Khi người dùng thực hiện hành động yêu cầu tài nguyên, ứng dụng sẽ gửi token đến các dịch vụ khác để xác thực quyền truy cập.
5. **Dịch vụ kiểm tra token**: Các dịch vụ xác thực token và cho phép hoặc từ chối yêu cầu dựa trên thông tin trong token.

### Kết Luận

- **Keycloak** là công cụ quản lý danh tính và phát hành token.
- **OAuth2** là giao thức giúp quản lý quá trình ủy quyền và sử dụng token để xác thực quyền truy cập.

Việc kết hợp Keycloak và OAuth2 giúp bảo mật ứng dụng của bạn, đồng thời cung cấp trải nghiệm người dùng tốt hơn thông qua quy trình đăng nhập và quản lý quyền truy cập hiệu quả.