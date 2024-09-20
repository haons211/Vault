
2024-09-20 20:06

Status:

Tags:
MindSet : Nỗi đau, vấn đề nào khiến cái này tồn tại.
KeyWord học thuật toán : Rule

# 20 Sep Webinar WeCommit
![[Pasted image 20240920211858.png]]
Khi học một lĩnh vực gì mới ? 
- Câu hỏi what đầu tiên ? Thuật toán là gì ?
     -   Thuật toán bắt đầu từ con người . Từ thế kỉ 19 người ta đưa ra 1 cách tuần tự : pha trà kiểu gì , nấu kiểu gì . Thế kỉ 20 , Turing đưa thuật toán vào máy tính . 
     - Thuật toán tách bài toán lớn thành các bài toán nhỏ .
          => Thuật toán vô cùng gần gũi
-  Người ta đánh giá thuật toán qua cái gì ?
    -  Độ phức tạp .(Trường hợp tệ nhất có thể xảy ra) 
    -  Quan trọng nhất thuật toán phải hiểu bản chất của nó : Quan trọng nhất là đúng. Còn lại là : Nhanh và nhẹ, dễ triển khai , maintain.
-  Có cách tiếp cận giải thuật nào ? khi có cái này , học mọi giải thuật khác khong ?
      -  Mảng và danh sách liên kết : 
      - a Huy : khi học 1 thứ gì đó . Đặt câu hỏi nó là gì ? Bản chất của nó là gì ? Nó giải quyết bài toán gì ? Ưu điểm , Nhược Điểm nó là gì?
    ### ARRAY - NHANH - TRỰC TIẾP (do cùng kích thước và liên tiếp)
      - Tại sao nó nhanh 
      -  Tập hợp dữ liệu , thông tin có cùng kiểu và nó ở cạnh nhau.
      - Cùng kích thước, liên tiếp
         Vị trí i = địa chỉ bắt đầu i*kích thước(32bit).
         Truy cập : O(1)
    - Nhược điểm : nó ở cạnh nhau : nên phải cấp phát bộ nhớ trước cho  nó và phải nằm gần nhau .
     -==> Ưu điểm cũng là nhược điểm lớn nhất : liên tiếp
     - khi muốn cấp phát dữ liệu, hệ thống phải cấp phát 1 loạt page liên tiếp nhau . Bản chất cấp phát database và mảng tương tự nhau .(fragmentation)
     -  Cùng kích thước (điểm yếu, điểm mạnh)
     - phần lớn object cố định . nhưng string ko phải cố định : tùy chữ dài, chữ ngắn . 
     - Làm sao để chuyển 1 thằng ko cố định thành cố định ?: dùng con trỏ  để lưu? lưu vị trí nên nó cố định .
    ### LinkedList - LINH HOẠT - CON TRỎ - THAM CHIẾU
     #### Nó là gì ? (khắc phục nhược điểm của ARRAY)
     ![[Pasted image 20240920205143.png]]
       #### LINH HOẠT
	   - Tập hợp các dữ liệu có thể liên kết được với nhau . Tại sao cách thiết
       kế này lại khắc phục ? 
       Ưu điểm : dùng tối ưu vùng nhớ ví các node lưu vị trí của thằng node sau nó.
       Dễ dàng thêm.(thứ tự thêm chuẩn) ![[Pasted image 20240920205801.png]]

     -  Vì mỗi lần tạo ra đều có thêm 1 vùng nhớ mỗi node để chứa vị trí . 
     -  Máy tính 32bit và 64bit : vị trí mỗi ô nhớ là 32bit và 64bit
     -  Di chuyển quá nhiều , tốn quá nhiều nguồn lực . Do thứ tự không gần nhau, nên phải nhảy đi nhảy lại (ngày trước, nhưng h đỡ hơn). Do có ổ SSD giải quyết được vấn đề HDD
    ### Vậy 2 kiểu này có áp dụng được nó với kiểu Graph hay gì đó không ?
    - Câu trả lời là có .
    - Queue(Thông tin , quan hệ) : Queue vòng, Queue Dồn
    -  Dữ liệu rời rạc và dữ liệu có quan hệ. 
    - Đồ thị là 1 dạng dữ liệu có quan hệ. ĐỒ thị là linkedlist nhưng thay vì trở 1 thằng, thì ở graph là trỏ nhiều thằng .

![[Pasted image 20240920211404.png]]

Định là data, cạnh là ô lưu vị trí.


-  Ma trận kề : Array + 1 luật
- Danh sách đỉnh kề : Array + 1 luật
- Danh sách cạnh : Array + 1 luật
Trải nghiệm khi pv với đồ thị : dễ dàng nhất là Ma trận kề.
### Vừa mới bắt đầu nên đi từ luật gì ?
     - Đảm bảm mình đúng đầu tiên.
     - Chỉ cần giải thuật vét cạn (trong database là full table scan).
     - Muốn vét cạn nhanh thì phải giảm vùng tìm kiếm : 
     - + Sắp xếp : đảm bảo dữ liệu có quy luật
### HashMap

Bài toán : từ value  ra index thế nào?

![[Pasted image 20240920213233.png]]
![[Pasted image 20240920213342.png]]
- Couting Sort : Cô giáo chấm điểm thi học sinh . Dùng trực tiếp index này làm giá trị luôn.
### Giải thuật mang lại điều gì ?
#### Mindset ?
-  Tôi muốn tôi ngon , không phải giỏi mới là ngon.
-  Không coi rằng trở thành chuyên gia là ưu tiên số 1 . Tôi muốn tổng của tôi là ngon nhất
-  Hãy xem mình là hình chữ nhật . Mục đích là diện tích rộng hơn . chứ không phải chỉ ưu tiên 1 góc.
-  Hãy trở thành key person.
- Tư duy gốc về giải thuật :
- Nắm rõ OOP và Solid
-  Đôi khi kiểm tra thuật toán xem kĩ năng giao tiếp như nào ? có thể hợp tác với nhau không
-  
### Tip
-  hỏi người phỏng vấn xem contraints như nào
- Stack Quêue,Graph, Cây nhị phân, hashmap, Vét cạn.Top k element., đệ quy, two pointer

Phân tích và thiết kế hệ thống
- Bạn đang có bao nhiêu thông tin?
-  Tiêu chí đánh giá khi thiết kế : - mở rộng thông tin đầu vào ?
-  Xem nhiều thằng khác làm ? để mình bít nó làm như nào








# References





