
# Giới thiệu về Zeek

Zeek (trước đây là Bro) là một công cụ giám sát mạng và phân tích lưu lượng mạng mã nguồn mở và thương mại được phát triển bởi Lawrence Berkeley Labs. Hiện nay, Zeek được hỗ trợ bởi nhiều nhà phát triển và Corelight cung cấp một phiên bản Zeek thương mại sẵn sàng cho doanh nghiệp. Công cụ này được gọi là mã nguồn mở và thương mại vì có cả hai phiên bản. Sự khác biệt giữa phiên bản mã nguồn mở và phiên bản thương mại được thảo luận ở đây.

## Sự khác biệt giữa Zeek và Snort

| Công cụ | Zeek | Snort |
|---------|------|-------|
| Khả năng | Khung NSM và IDS, tập trung mạnh vào phân tích mạng. Có khả năng phát hiện sự kiện. | Hệ thống IDS/IPS, tập trung mạnh vào các chữ ký để phát hiện lỗ hổng. Cơ chế phát hiện tập trung vào mẫu chữ ký và gói tin. |
| Nhược điểm | Khó sử dụng. Phân tích được thực hiện ngoài Zeek, bằng thủ công hoặc tự động hóa. Khó phát hiện các mối đe dọa phức tạp. | |
| Ưu điểm | Cung cấp khả năng nhìn thấu lưu lượng chi tiết. Hữu ích cho săn mối đe dọa. Có khả năng phát hiện các mối đe dọa phức tạp. Có ngôn ngữ kịch bản và hỗ trợ tổng hợp sự kiện. | Dễ đọc log. Dễ viết luật. Hỗ trợ luật của Cisco. Hỗ trợ cộng đồng mạnh mẽ. |
| Trường hợp sử dụng phổ biến | Giám sát mạng. Điều tra lưu lượng chi tiết. | Phát hiện và ngăn chặn xâm nhập. Dừng các cuộc tấn công/thuật toán biết đến. |

## Kiến trúc của Zeek

Zeek có hai lớp chính: "Bộ xử lý sự kiện" và "Trình thông dịch tập lệnh chính sách". Lớp Bộ xử lý sự kiện là nơi các gói tin được xử lý, chịu trách nhiệm mô tả sự kiện mà không tập trung vào chi tiết sự kiện. Lớp Trình thông dịch tập lệnh chính sách là nơi phân tích ngữ nghĩa được tiến hành, chịu trách nhiệm mô tả các sự kiện liên quan bằng cách sử dụng các kịch bản Zeek.

## Các Framework của Zeek

Zeek có nhiều framework để cung cấp các chức năng mở rộng trong lớp kịch bản. Các framework này tăng tính linh hoạt và tính tương thích của Zeek với các thành phần mạng khác. Mỗi framework tập trung vào một trường hợp sử dụng cụ thể và dễ dàng chạy với cài đặt Zeek. Ví dụ, chúng ta sẽ sử dụng "Khung Logging" cho tất cả các trường hợp. Hiểu về chức năng của từng framework có thể giúp người dùng nhanh chóng xác định một sự kiện quan trọng.

**Các Framework có sẵn:**
- Logging
- Notice
- Input
- Configuration
- Intelligence
- Cluster
- Broker Communication
- Supervisor
- GeoLocation
- File Analysis
- Signature
- Summary
- NetControl
- Packet Analysis
- TLS Decryption

## Đầu ra của Zeek

Zeek cung cấp hơn 50 tệp log trong bảy danh mục khác nhau, hữu ích trong nhiều lĩnh vực như giám sát lưu lượng, phát hiện xâm nhập, săn mối đe dọa và phân tích web. Phần này không nhắm đến việc thảo luận chi tiết về các log.

## Làm việc với Zeek

Có hai tùy chọn hoạt động cho Zeek. Tùy chọn đầu tiên là chạy nó như một dịch vụ và tùy chọn thứ hai là chạy Zeek trên một file pcap. Trước khi bắt đầu làm việc với Zeek, hãy kiểm tra phiên bản của Zeek với lệnh sau: `zeek -v`

Bây giờ chúng ta có thể khởi động Zeek như một dịch vụ! Để làm điều này, chúng ta cần sử dụng mô-đun "ZeekControl", như đã thể hiện dưới đây. Mô-đun "ZeekControl" yêu cầu quyền siêu người dùng để sử dụng.

**Sử dụng mô-đun ZeekControl:**
```bash
sudo su
zeekctl
[ZeekControl] > status
[ZeekControl] > start
[ZeekControl] > stop
```

Chúng ta cũng có thể sử dụng mô-đun "ZeekControl" với các lệnh sau:
- `zeekctl status`
- `zeekctl start`
- `zeekctl stop`

Để nghe lưu lượng mạng trực tiếp, chỉ có cách duy nhất là sử dụng Zeek như một dịch vụ. Ngoài việc sử dụng Zeek như một công cụ giám sát mạng, chúng ta cũng có thể sử dụng nó như một công cụ điều tra gói tin. Để làm điều này, chúng ta cần xử lý các file pcap với Zeek. Sau khi xử lý một file pcap, Zeek sẽ tự động tạo các tệp log theo lưu lượng.

**Xử lý pcap với Zeek:**
```bash
zeek -C -r sample.pcap
```

Log được tạo ra sẽ được lưu trong thư mục làm việc. Bạn có thể xem các log được tạo bằng lệnh `ls -l`.

Đó là một cái nhìn tổng quan về Zeek, một công cụ mạnh mẽ trong lĩnh vực giám sát và phân tích mạng.


### Trả lời câu hỏi
