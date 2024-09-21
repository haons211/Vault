2024-09-18 14:53

Tác giả :  Trần Quốc Huy - Databases

Link :  https://www.youtube.com/watch?v=xC1662uBym8

tags: [[Database]], [[Learning]]
# Note


- Để hiểu toàn bộ database nguyên lí 3 + 2 : 3 nguyên lí , 2 cơ chế .
- Áp dụng nguyên lí đó vào phát triển sự nghiệp. 
- Không cần nhảy việc mà vẫn tích lũy được kinh nghiệm .
#### 1. NGUYÊN LÍ 3 + 2
##### Nguyên lí 1 : Pages / Block
 - Cách cũ : Cơ bản + where (giúp lọc dữ liệu)
 - Cách mới :  Tam giác để học mọi thứ trong database :
    + Pages/Block : Mức độ hoạt động nhỏ nhất, cách thức database lưu những bản ghi
	     - Dữ liệu những tờ A4, ta ghi dữ liệu mình vào các dòng trên tờ A4
	     - ![[Pasted image 20240921090604.png]]
	     - Database như quyển sổ , gồm rất nhiều tờ giấy.
	     -  1 bảng có ít bảng ghi hay nhiều ko quan trọng. Quan trọng là có bao nhiêu tờ A4.
	     - Tại sao hệ thống lại chậm ? Tại vì phải trải qua nhiều page.
	     = >> Tư duy tối ưu : Giảm số page, block (Giảm số trang sách, mà kiến thức vẫn y nguyên)
    + 

##### Nguyên lí 2 : Cache và 2 cơ chế Read&Write trong database
- Dữ liệu phải lưu ở chỗ nào đó , mà người trước lấy ra rồi thì người sau phải lấy ra nhanh hơn.
-  Như chúng ta đã biết, đơn vị nhỏ nhất của database là pages/ block . Vậy cache thì sẽ cache cái gì ? Không phải bản ghi , mà là 1 pages . Vậy chúng ta đã lấy những thông tin thừa thải bên ngoài bản ghi cần thiết , gây tràn bộ nhớ với hệ thống lớn .
 ==> Mục tiêu Cache : Đưa tất cả bản ghi về 1 pages/block
 - 

#### 2. CÁCH ÁP DỤNG TƯ DUY VÀO SỰ NGHIỆP, CUỘC SỐNG .


1. [Nguyen Van A](Goog read)
2. 
