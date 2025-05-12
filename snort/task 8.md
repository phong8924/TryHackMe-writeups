## Phân tích PCAP với Snort
Snort không chỉ dùng để giám sát mạng theo thời gian thực mà còn có thể phân tích tệp PCAP ở chế độ ngoại tuyến. Khi xử lý PCAP, Snort cung cấp thống kê lưu lượng và cảnh báo dựa trên bộ quy tắc đang dùng. Việc sử dụng các tham số phù hợp giúp tận dụng tối đa khả năng phát hiện mối đe dọa từ các mẫu đã biết, hỗ trợ quá trình điều tra hiệu quả hơn. Đây cũng là bước chuẩn bị quan trọng trước khi bắt đầu viết quy tắc cho Snort.
## Key Parameters for IDS/IPS Mode

| Parameter | Description |
|-----------|-------------|
| `-r / --pcap-single=`      | Đọc một pcap duy nhất |
| `--pcap-list=""`      | Đọc pcaps được cung cấp trong lệnh (cách nhau bằng dấu cách). |
| `--pcap-show`      | Hiển thị tên pcap trên bảng điều khiển trong quá trình xử lý. |

**Ví dụ**
`sudo snort -c /etc/snort/snort.conf -q -r icmp-test.pcap -A console -n 10`

| Tham số | Ý nghĩa |
|-----------|-------------|
| `-r icmp-test.pcap` | Đọc dữ liệu từ file pcap. Ở đây, Snort sẽ phân tích file icmp-test.pcap. |
| `-A console`      | Hiển thị cảnh báo (alerts) ra màn hình console thay vì ghi vào file log hoặc syslog. |

#### Trả lời các câu hỏi :
>**1:** Kiểm tra tệp mx-1.pcap bằng tệp cấu hình mặc định.
`sudo snort -c /etc/snort/snort.conf -A full -l . -r mx-1.pcap`
Số lượng cảnh báo được tạo ra là bao nhiêu?
![alt text](<../png/snort-task8 (1).png>)

>**2:** How many "HTTP response headers" were extracted?
![alt text](<../png/snort-task8 (2).png>)

>**3:** How many "HTTP response headers" were extracted?
![alt text](<../png/snort-task8 (3).png>)

........................................................
