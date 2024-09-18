
2024-09-18 10:20

Status:

Tags:


# Untitled

### Vấn đề khi unboxing và boxing
    Vấn đề về hiệu xuất do . Do chuyển từ Reference sang Primitive
{}

```Csharp
swap(T a, T b)
{
   T t;
   t = a;
   a = b;
   b = t;
}
```



      Icomparer<T> : cho 2 object cần phải so sánh , bạn phải định nghĩa cho nó để biết được so sánh theo cái nào .
      Cơ chế Băm : Mỗi khi cho vào 1 value, thuật toán sẽ băm ra 1 hashkey . Nếu trùng sẽ tiếp tục băm cho đến khi có 1 key khác.
       Áp dụng vào lúc tìm kiếm : học sinh "Nguyễn Văn A" mã sinh viên bao nhiêu .
       
```C shark

         Hashtable hashTable = new HashTable();
         hashTable.add("HE21313","Nguyeênễn Vaăn A")
         hashTable
         
 
# References





