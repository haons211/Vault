- Cách học cũ : Học từ đến khó , Khiến tầm nhìn mình bị hạn hẹp. Không phát triển
- Cách học của Trần Quốc Huy : (Tiếp cận từ output)
  - Hiểu ra output nào mình cần . Cái mình cần cuối cùng là liên quan đến độ hiểu biết .
  - Đi đến những ơi họ đã biết rồi. Tôi đến tôi tìm ông này để mình có level của người ta .
  - Mình học database : output cuối cùng, ở dự án hiện nay của database họ làm gì ngoài kia, chứng khoán, ngân hàng  làm gì ở ngoài kia .
  - Chú Huy : Ngoài kia có mấy mô hình  thôi 
    - 1 thằng database đứng 1 mình , gọi là standalone
    - ![[Pasted image 20241011201406.png]]
    - Coi các cụm thành 1 database(Cluster),hay trong Oracle gọi là Oracle RAC.    - ![[Pasted image 20241011201518.png]]
    - Có  những thứ còn phức tạp hơn nữa, hệ thống trọng yếu, core banking
    ![[Pasted image 20241011201653.png]]
    - Người ta để ra thêm nhiều cụm nữa, đặt ở nơi khác:
    - ![[Pasted image 20241011201826.png]]
    - Người ta lấy 1 phần tí tí vào cái database màu xanh, ko phải toàn bộ.![[Pasted image 20241011201927.png]]
    - =====> Đích đến đây rồi.
-  Người Who là điểm bắt đầu khi tôi bắt đầu học.
- Tìm đủ lí do đến sớm, chỉ để có thời gian nói chuyện để xem công ty như nào
- Có hôm ở lại dọn dẹp, càng ở gần người giỏi thì càng dễ.
- Khi đã có bức tranh rồi thì . Quay lại tìm hiểu thật kỉ 
- ---> Quay lại tìm hiểu thành standalone
### Khi tìm hiểu 1 thằng database
- Bóc tách nhỏ nó ra để tìm hiểu .
- Chúng nói với nhau bằng  ngôn ngữ SQL.
- Vậy khi gửi đến database câu lệnh SQL thì các gì xảy ra?![[Pasted image 20241011202454.png]]
- Lúc này phải nhớ đến output không lan man . Các chúng ta học ở đây là để ghép vào bức tranh lớn, chứ không phải lung tung . 
- Câu lệnh "SELECT * FROM" : nó phải thực hiện cái gì đấy, thằng database phải chọn ra con đường nào có chi phí nhỏ nhất để nó thực hiện .![[Pasted image 20241011202723.png]] ( vùng khoanh là shared pool)
- -> Bọn này có 1 cái vùng chuyên làm các việc lưu lại -> Database BufferCache. Buffer Cache sinh ra để hứng kết qủa từ nhiều câu lệnh.![[Pasted image 20241011203023.png]]
- Dữ liệu có thể lưu ở các ô. Khi insert hay gì đó thì nó sẽ chuyển sang màu khác. database sẽ hiểu đó không được đưa cho người dùng nữa. Các ô đó là block.
- Vậy tại sao lại dùng block? Trần Quốc Huy mò 1 lúc ra bản chất database . Block/Page có 8kb.
- Làm sao dữ liệu thay đổi . Tạo ra 1 vùng lưu dữ liệu thay đổi. (redu buffer)![[Pasted image 20241011203348.png]]
### Tổng quan kiến trúc của database
![[Pasted image 20241011203432.png]]
   ->Vùng này  là memory (lí do người ta chọn memory cao)
   
Nhiều quá ! Tôi phải chọn cái gì đây ? Tôi phải hỏi anh Who? 
- Học đi từ cái tên : bufferCache : lưu tạm . Tại sao lại là block. Tôi dùng ông Who để tiết kiệm thời gian

Lưu hết trên memory thì có mà toang . keyword : Datafile. 
Câu hỏi : Bufer Cache và datafile phải liên quan đến nhau ?
  - DataFile như quyển sổ gồm rất nhiều trang A4. Thông tin là các dòng viết trên trang giấy đó![[Pasted image 20241011203931.png]]
  - Tìm hiểu nâng cao (có thể custome các block) : nhưng 90% Không cần . ![[Pasted image 20241011204052.png]]
     (Tổng quan lúc này)
- Vậy thằng redoo buffer cũng phải có nơi lưu chứ . Người ta lại sinh ra.![[Pasted image 20241011204204.png]]
-Sinh ra theo nguyên tắc đổ đầy 1-2-3-1-2 . Nó đổ đầy vòng tròn . Vậy đổ 3 xon đổ lại 1 thì lại mất à ?
- Sinh ra Archive log = Backup của Redo log![[Pasted image 20241011204327.png]]
   (Các file này cứ ghi vào , nhưng không ghi đè nữa)
===> Nguyên tắc Backup của Backup . Người ta sinh ra để đối phó với những trường hợp khẩn cấp, thiên tai. Cần được khôi phục.
### Quay lại với bản chất 
![[Pasted image 20241011204519.png]] Bạn thấy đấy, có rất nhiều back-up.
### Làm sao đồng bộ dữ liệu từ HN và HCM.
- Nó đưa Archive Log và Redo Log để đồng bộ. (Nó là các mũi tên vàng)
### Sự cố nào?
- Ông HCM mất điện 1 ngày. Ông HN sinh ra 1 đồng Archive Log và Redo Log . mà lí do nào đấy xóa cmn 2 thằng . Thì lấy đâu mà đồng bộ .
- ![[Pasted image 20241011204826.png]]
### Vậy làm sao để đồng bộ dữ liệu ?
- Golden Date và Data Guard
==> File Log rất quan trọng.
- Trong hệ thống có thể có nhiều datafile
- ![[Pasted image 20241011205318.png]]
### Cần sinh ra 1  thứ để quản lí 
==> Control File : Nó là tấm bản đồ của toàn bộ hệ thống![[Pasted image 20241011205420.png]]
   (Nó là vị tướng) => Mất tướng thì bại trận.
### Tổng Quan 
![[Pasted image 20241011205517.png]]
#### File gì đó để quy định Ram 
==> ParamentFile : Ghi hiệu năng 
![[Pasted image 20241011205638.png]]
## Tổng Quan
![[Pasted image 20241011205719.png]]

- Bên trên lưu ở Memory
- Bên dưới chứa ở OS.
### Vậy mấy cái file ở OS nằm ở đâu ?
### Ocracle RAC là gì ?
- bắt đầu mô hình cluster . với 2 Database.![[Pasted image 20241011210028.png]]
   (2 thằng này memory)
- DataFile nằm ở 1 chỗ khác . ![[Pasted image 20241011210148.png]]
- Phải cấp phát 1  thiết vị lưu trữ riêng cho Data File => SAN (Anh em phải bỏ tiền mua)
- Thằng Oracle chỉ đưa ra 1 đưa địa chỉ Ip thoi . Do là cluster![[Pasted image 20241011210344.png]]
- Điểm quan trọng nhất , có kênh gì đó truyền dữ liệu giữa 2 thằng db ==> Inter Connect![[Pasted image 20241011210505.png]]
- Đường Inter Connect phải là 1 đường riêng (Hãng cảnh cáo)
- Bọn db phải nối với nhau . Số node càng tăng lên . Nối càng nhiều . 
- Kinh nghiệm . Số node lẻ gà hơn Số nốt chẵn 2 hoặc 4
### Tổng quan mô hình Oracle RAC
![[Pasted image 20241011210810.png]]
# Cách học 
+ Who
+ Output
# Tổng Quan từ đầu 
![[Pasted image 20241011211042.png]]
# Tại sao Trần Quốc Huy học database?
- Tiền
# Cách học 1 biết 10 trong việc kiếm tiền.
### Tư duy mới là cái cách kiếm tiền.
- Tư Duy Cũ :![[Pasted image 20241011211615.png]]
- Tư Duy Mới :![[Pasted image 20241011211732.png]]
=======> Giá trị >>> Tiền.![[Pasted image 20241011212152.png]]

- Tức là sao ? Tôi chỉ quan tâm đến giá trị . Tiền tôi nhận luôn thấp hơn giá trị tôi tạo ra . 
- Tôi không tìm cách nhảy việc . Tôi tìm cách tăng giá trị tôi làm ra.
- Mình ngon ko chỉ tạo ra nhiều giá trị . Ngon vì người ta nhớ đến mình nhiều hơn.
### Cách đám đông họ đang làm ?
- ![[Pasted image 20241011212807.png]]
Cty B lương cao hơn . Nhảy sang
- Nhảy không phải là vấn đề. Tư duy có vấn đề ?
=> Tư duy ManDay . Sức lao động tính là tiền . Họ không còn thời gian nào . Không còn thời gian ? Không tăng được nữa, đến 1 ngưỡng họ sẽ giảm giá trị .
### Làm sao để đi theo cái đường màu vàng ?
![[Pasted image 20241011211732.png]]
- Họ đã làm với tôi rồi thì phải nói là Ngon . Tôi làm mọi thứ vì cái output này  . Ông đã dùng. Ông không muốn dùng người khác .
- Công ty là 1 khách hàng của mình . Ngay lập tức mình trở thành người khởi nghiệp.
- Anh em hiểu sai, dữ liệu nhiều bản ghi thì chậm ?
- Khi chúng ta làm 1 điều khác với người khác? Đa số bị ăn chửi.
- Tôi phải trao cho nhiều người ? Tôi phải nói cho người khác biết .  
> Không cần nhiều tiền để tạo ra giá trị để tạo nên câu chuyện. Chúng ta cần chiến lược, quyết tâm để tạo ra sự khác biệt.
- Chúng ta làm gì đi nữa? Sẽ có người không tin . Đó là điều bình thường . Chúng ta có cách thức biến điều đó thành lợi thế.
- Chúng ta là người nhiệt tình. Chúng ta phải là người cho đi
- Chúng ta cho 10 và đòi 1, không thì cho 5 đòi 1.
### Tại sao lại chia sẻ giá trị cho người khác , anh em bị hâm à ?
- Tôi làm vì output của tôi. 
- Tôi không nhìn hiện tại. Tôi nhìn tương lai
### Chiến lực kết nối với Who
- Ông đấy có cái mẹ gì ? mua hết , khóa học gì ....
- Tìm Who của Who. Mình cần gặp ai để có thể giúp mình tìm được ông Who kia.
- 
