
2024-09-30 16:40

Status:

Tags: [[AWS]] [[Learning]] [[Storage]]


# Storage trong AWS

     Trong AWS các loại lưu trữ được chia làm 2 nhóm chính : Network-attached storage (lưu trữ gắn kết qua mạng) và hardware-base storage)

### 1.  Network-attached storage 
   - Vì lưu trữ qua mạng nên nó sẽ hoạt động độc lập với các EC2 instance hay nói cách khác, khi một con EC2 không hoạt động thì cũng không ảnh hưởng gì cả.
#### 1.1 EBS (Elastic Block Store) - Ổ đĩa ảo
 - EBS là một dịch vụ lưu trữ dạng block, hoạt động giống như một ổ đĩa cứng ảo cho EC2 instance .
 -  Trong một thời điểm trong cùng 1 AZ , mỗi EBS có thể được gắn với 1 EC2 intance , ngược lại 1 EC2 có thể gắn với nhiều EBS 1 lúc. 
#### 1.2 EFS (Elastic File System) - Hệ thống tệp
 -  EFS là dịch vụ lưu trữ dạng file
 - Nhiều EC2 instance trong cùng một **Region** có thể gắn kết và sử dụng cùng một hệ thống tệp EFS đồng thời. Phù hợp với các ứng dụng cần chia sẻ tệp giữa nhiều máy chủ.
   
         EBS và EFS sinh ra cho những mục đích khác . Có thể nói EBS sinh ra thuần lưu trữ cho những ứng dụng đơn lẻ (1 EC2 duy nhất,CSDL) . EFS phù hợp cho ứng dụng chia sẻ tệp giữa nhiều instance.
### 2. Hardware-Based Storage 
- Lưu trữ cục bộ trên ổ đĩa vật lý được gắn trực tiếp vào máy chủ nơi EC2 instance của bạn đang chạy .
-  Vì được gắn trực tiếp vào EC2 instance nên mỗi khi EC2 của bạn bị dừng hoặc hỏng, dữ liệu sẽ bị mất
-  Không thể mở rộng dung lượng
-  **Tốc độ rất nhanh**: Do dữ liệu được lưu trữ trực tiếp trên phần cứng vật lý, Instance Store có tốc độ đọc/ghi rất cao, lý tưởng cho các tác vụ tạm thời và có yêu cầu về hiệu suất cao (như xử lý dữ liệu tạm thời).
# References





