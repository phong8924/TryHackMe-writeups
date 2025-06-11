### Các tính năng của Wireshark trên dòng lệnh | Thống kê

TShark được coi là phiên bản dòng lệnh của Wireshark. Ngoài việc chia sẻ các bộ lọc hiển thị giống nhau, TShark còn có thể thực hiện một số tính năng của Wireshark được giải thích dưới đây.

#### Ba điểm quan trọng khi sử dụng các tính năng giống Wireshark:
1. Các tùy chọn này được áp dụng cho tất cả các gói trong phạm vi trừ khi có bộ lọc hiển thị được cung cấp.
2. Hầu hết các lệnh được hiển thị dưới đây là phiên bản CLI của các tính năng Wireshark đã được thảo luận trong Wireshark: Packet Operations (Task 2).
3. TShark giải thích các tham số được sử dụng ở đầu dòng kết quả.

Ví dụ: bạn sẽ sử dụng tùy chọn `phs` để xem phân cấp giao thức. Khi sử dụng lệnh này, kết quả sẽ bắt đầu với tiêu đề "Packet Hierarchy Statistics".

---

### Các tham số và mục đích:
- `--color`: Hiển thị đầu ra có màu giống Wireshark.
  ```bash
  tshark --color

-z: Thống kê. Có nhiều tùy chọn có sẵn dưới tham số này. Bạn có thể xem các bộ lọc có sẵn bằng:
Hiển thị màu sắc
TShark có thể cung cấp đầu ra có màu để giúp các nhà phân tích nhanh chóng phát hiện các bất thường. Tùy chọn này được kích hoạt với tham số --color.

Ví dụ:

Thống kê | Phân cấp giao thức
Phân cấp giao thức giúp các nhà phân tích xem các giao thức được sử dụng, số khung và kích thước gói trong dạng cây. Nó cung cấp tóm tắt về dữ liệu thu thập, giúp xác định điểm tập trung cho sự kiện quan tâm.

Lệnh:

Kết quả sẽ hiển thị phân cấp giao thức. Bạn cũng có thể tập trung vào một giao thức cụ thể bằng cách thêm từ khóa (ví dụ: udp) vào bộ lọc.

Thống kê | Cây độ dài gói tin
Cây độ dài gói tin giúp các nhà phân tích xem phân phối chung của các gói theo kích thước. Nó cho phép phát hiện các gói lớn hoặc nhỏ bất thường.

Lệnh:

Thống kê | Điểm cuối
Thống kê điểm cuối giúp các nhà phân tích xem các điểm cuối duy nhất và số lượng gói liên quan đến từng điểm. TShark hỗ trợ nhiều định dạng lọc nguồn cho việc xác định điểm cuối.

Ví dụ:

Thống kê | Cuộc hội thoại
Thống kê cuộc hội thoại giúp các nhà phân tích xem luồng dữ liệu giữa hai điểm kết nối cụ thể.

Lệnh:

Thống kê | Thông tin chuyên gia
Thông tin chuyên gia giúp các nhà phân tích xem các nhận xét tự động do Wireshark cung cấp. Lệnh:

Kết quả sẽ hiển thị các ghi chú và thông tin chi tiết về các sự kiện trong dữ liệu thu thập. ```