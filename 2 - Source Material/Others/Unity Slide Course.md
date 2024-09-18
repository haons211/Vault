
2024-09-18 15:54

Teacher : 

Course Material : 

Tags: 
 Điểm chung  : - Các method thông thường sẽ viết hoa tất cả các chữ : ví dụ

# Unity Slide Course

### 1.1 Introduction to Unity Interface and Navigation
   - Unitiy is cross-platform game realeased in 2005.
-  Layout of Unity : Được thiết kế linh hoạt , thân thiệt với người dùng , co thể custom được dựa theo drag hoặc rearrange window
-  Unity Inteface Component:
     -  A Toolbar : cung cấp truy cập tới account và cloud service
     -  The Hierarchy window : trình bày phân cấp của tất cả đối  tượng game (game Object)
     -  The Game view : mô phỏng góc nhìn cuối cùng của game khi hoàn thiện. Khả năng play, pause, ...
     -  The Science view : cho phép edit your Scene. Có các tool để moving, rotating , camera control
     - Overlay :
     - The Inspector window : cho phép bạn xem và chỉn sửa các thuộc tính cua GameObject bạn chọn hiện tại
     - Thr Project window : Hiển thị thư viện asset có trong Poject của bạn
     -  The status bar : nơi hiện thông báo

### 1.2 Basic Game Object Manipulation and Transformation
- GameObject là components nền tảng trong mọi Unity game project . Mọi đối tượng trong game đều là GameObject từ chữ , ánh sáng, camera cho đến các hiệu ứng đặc biệt. 
##### Hierarchy Panel - GameObjects - Nested
-  GameObject cha có thể có nhiều GameObject con . Các GameObject con được tiếp nhận của thuộc tính của cha
- GameObject con chuyển đồng, xoay, scale chính xác như những gì cha nó đã làm . GameObject con có  thể có thể có con khác . nhưng tất cả chỉ duy nhất có một parent GameObject
##### Transform 
 - Là nơi lưu trữ các thuộc tính của GameObject như Position, Rotation, Scale and các parenting state.
##### Understanding 3D coordinate 
 - Unity uses a left-handed coordinate system áp dụng cho nhiều chương trình 3D
##### Local vs world coordinate space
- Mỗi đối tượng trong Unity đều có ví tri , nhưng vị trí ấy cần hệ tham chiếu . Trong Unity có 2 loại coordinate:
     -  World coodinates : Vị trí đối tượng đặt trong toàn thế giới
     -  Local coodinates : Ví trí đối tượng nằm trong lớp cha của nó.
### 1.3 Understanding Unity's Component System
##### What is Unity's Component System ?
- Entity là core của Unity công nghệ hướng dữ liệu . ESC có 3 nguyên tắc :
   - Entity : Là thực thể trong game : OOP
   -  Components: Là dữ liệu liên quan đến thực thể : DOP
   -  Systems: Cập nhập vị trí, trạng thái của Entity . Xử lí liên quan đến logic liên quan các trọng thái khác
   - ![[Pasted image 20240919054742.png]]
=>  GameObject ---- Component ---- Variable (1 gameObject có nhiều Component và bên trong Component ấy có thể chứa các giá trị để chỉnh sửa)
##### Comom Components in Unity 
![[Pasted image 20240919054916.png]]

##### Advantages of Component- Based Design
- Ease of deployment : Dễ dàng thay thế các version cũ đế sang version khác mà khong lỗi.
- Reduced cost : 
- Ease of development:
- Reusable
-
### 1.4 Scence Creation and Management
##### What are scenes in Unity ?
 -  Scences are where you work with content in Unity. They contains all or part of a game or application
##### Working with Scenes
- Sence View cho việc visual editing , Hirrarchy panel cho việc structured of GameObject
##### Navigating Between Scenes
- UnityEngine. SceneManagement provides functionalities for managing scence including switching between them, adding/ removing scenes , and controlling their state .
     - Loading Scenes : LoadScene()
     - Unloading Scences : UnloadScene() 
     - Scence Switching : SceneManager. LoadScene()
##### Scene Lighting and Camera Setup 
- Three main types are point , spot , directional.
     -  Point : like a light bulb in the world . The light is brighter up close . You can you them để mô phỏng 1 vụ nổ 
     -  Spot : Ánh đèn, đèn rọi . Tất cả các tia sáng từ 1 single point
     - Diractional : tất cả tia sáng đều song song, thắp sáng mọi thứ theo cùng 1 cách . tương tự như mặt trời cùng thế giới
##### Player Configuration
- Per-Platform Settings
    -  Resolution and Presentation
    - Icon
    - Splash Image
    - Other Setting
### 1.5 Introduction to Physics and Colliders
##### Importance of Physics in Game
   -  Realism Enhancement : 
      - Simulation of Real-World
      - Enviroment Interaction
   -   Improving Interactivity:
     - Dynamic Interactions:
     - Player Agency
##### Unity's Built- in Physics Engine
- Built in 3D physics (Nvidia engine intergration)
-  Built in 2D physics (Box2D engine intergration)
# References





