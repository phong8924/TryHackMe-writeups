# NetworkMiner Tổng Quan Nhanh

## Khả Năng

| **Chức Năng**                  | **Mô Tả**                                                                 |
|-------------------------------|---------------------------------------------------------------------------|
| Sniffing Giao Thức            | Chặn, đánh hơi và ghi lại các gói dữ liệu đi qua mạng.                   |
| Phân tích file PCAP           | Phân tích các file pcap và hiển thị nội dung chi tiết của các gói tin.   |
| Phân tích giao thức           | Xác định các giao thức được sử dụng từ file pcap đã phân tích.           |
| Nhận dạng hệ điều hành        | Xác định hệ điều hành sử dụng dựa trên dữ liệu pcap (dựa vào Satori và p0f). |
| Trích xuất tệp tin            | Trích xuất hình ảnh, file HTML và email từ file pcap.                     |
| Trích xuất thông tin đăng nhập| Trích xuất thông tin đăng nhập từ file pcap.                              |
| Trích xuất từ khóa văn bản rõ | Trích xuất từ khóa và chuỗi văn bản rõ từ file pcap.                      |

## Chế Độ Hoạt Động

NetworkMiner có hai chế độ hoạt động chính:

1. **Chế độ Sniffer**: Chủ yếu được sử dụng cho phân tích pháp chứng mạng thay vì đánh hơi chủ động. Tính năng sniffing chỉ hỗ trợ đầy đủ trên Windows.

2. **Phân tích/ Xử lý gói tin**: Cung cấp cái nhìn tổng quan nhanh chóng trong quá trình điều tra ban đầu, tập trung vào dữ liệu dễ truy cập.

## Ưu và Nhược Điểm

**Ưu điểm:**
- Nhận dạng hệ điều hành
- Trích xuất file dễ dàng
- Trích xuất thông tin đăng nhập
- Trích xuất từ khóa văn bản rõ
- Tổng quan mạng

**Nhược điểm:**
- Không hiệu quả khi đánh hơi chủ động
- Hạn chế khi phân tích file pcap lớn
- Khả năng lọc hạn chế
- Không phù hợp để điều tra gói tin thủ công

## So Sánh NetworkMiner và Wireshark

| **Tính Năng**                 | **NetworkMiner**                                         | **Wireshark**                             |
|-------------------------------|----------------------------------------------------------|-------------------------------------------|
| **Mục đích**                  | Tổng quan nhanh, ánh xạ lưu lượng và trích xuất dữ liệu  | Phân tích chuyên sâu                       |
| **Giao diện GUI**             | ✅                                                       | ✅                                         |
| **Sniffing**                  | ✅                                                       | ✅                                         |
| **Xử lý file PCAP**           | ✅                                                       | ✅                                         |
| **Nhận dạng HĐH**             | ✅                                                       | ❌                                         |
| **Tìm từ khóa/tham số**       | ✅                                                       | Thủ công                                  |
| **Trích xuất thông tin đăng nhập** | ✅                                               | ✅                                         |
| **Trích xuất file**           | ✅                                                       | ✅                                         |
| **Khả năng lọc**              | Hạn chế                                                  | ✅                                         |
| **Giải mã gói tin**           | Hạn chế                                                  | ✅                                         |
| **Phân tích giao thức**       | ❌                                                       | ✅                                         |
| **Phân tích payload**         | ❌                                                       | ✅                                         |
| **Phân tích thống kê**        | ❌                                                       | ✅                                         |
| **Hỗ trợ đa nền tảng**        | ✅                                                       | ✅                                         |
| **Phân loại máy chủ**         | ✅                                                       | ❌                                         |
| **Dễ quản lý**                | ✅                                                       | ✅                                         |

## Kết Luận

NetworkMiner cung cấp cái nhìn ban đầu và khả năng phân tích nhanh lưu lượng mạng, trong khi Wireshark cung cấp các công cụ phân tích chuyên sâu và kiểm tra giao thức chi tiết. Việc kết hợp cả hai công cụ thường là phương pháp tốt nhất trong điều tra pháp chứng mạng.

