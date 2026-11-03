**4\. Yêu cầu đầu ra**

***Phần 1\. Phân tích***

* Vẽ lại sơ đồ Box Model hiện tại của phần tử lỗi qua tab **Computed**.

margin: \-34px        (margin âm, kéo khung lấn lên vùng khác)

└─ border: bình thường

   └─ padding: bình thường

      └─ content: width 110%   (rộng hơn container 10%)

z-index: 99999       (nằm trên cùng mọi phần tử)

***Phần 2\. Triển khai***

* Đưa ra thông số CSS mới giúp sửa lỗi chồng lấn giao diện.  
- width : 100% để khung về đúng trong container, hai khung nằm cạnh thì chia đôi kiểu 48%  
- margin : \-34px đổi thành 0, muốn hai khung hở ra chút để 10px  
- z-index : 99999 xoá đi hoặc hạ về 1

***Phần 3\. Kiểm thử***

* Giả định thay đổi Margin nhưng phần tử vẫn không di chuyển, hãy kiểm tra xem có thuộc tính nào đang ghi đè ở tầng Browser Engine không?  
- Kiểm tra: Phần tử có đang ở dạng display inline hay không, các thẻ inline không nhận thuộc tính margin-top và margin-bottom.  
- Khắc phục: Chuyển thành display: inline-block hoặc display: block.  
  Xung đột vị trí :   
  Kiểm tra: Nếu phần tử đang bật position : absolute hoặc fixed, trình duyệt sẽ định vị dựa trên các thuộc tính tọa độ thay vì luồng tài liệu thông thường, khiến margin có thể không đẩy được phần tử theo ý muốn.  
- Khắc phục: Kiểm tra xem có đang thiếu top hoặc cần chuyển về position: relative  
  Ảnh hưởng từ Flexbox hoặc CSS Grid :  
- Kiểm tra : Nếu phần tử là một flex item, một số thuộc tính margin có thể bị chi phối bởi cơ chế căn chỉnh của Flexbox   
  Độ ưu tiên CSS hoặc important bị ghi đè :  
- Kiểm tra : Nhìn sang tab Styles, xem giá trị margin vừa nhập có bị gạch ngang hay không.