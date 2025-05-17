## Let's run Snort in Logger Mode
Có thể sử dụng Snort như một sniffer và ghi lại các gói tin đã sniff qua chế độ logger. Bạn chỉ cần sử dụng các tham số chế độ packet logger, và Snort sẽ thực hiện phần còn lại để hoàn thành việc này.

| Tham số | Mô tả |
|---------|------|
| `-v`    | Verbose - Hiển thị chi tiết TCP/IP trong console |
| `-d`    | Hiển thị payload (dữ liệu) của gói tin |
| `-e`    | Hiển thị header lớp liên kết (Ethernet, TCP/IP, UDP, ICMP) |
| `-X`    | Hiển thị toàn bộ nội dung gói tin ở định dạng HEX |
| `-i`    | Chọn giao diện mạng để sniff, ví dụ: `eth0` |

## Trả lời các câu hỏi:

Kiểm tra lưu lượng truy cập bằng tệp cấu hình mặc định  ở chế độ ASCII.

`sudo snort -dev -K ASCII -l . `

**Câu hỏi 1:** Thực thi tập lệnh tạo lưu lượng và chọn  `TASK-6 Exercise` . Đợi cho đến khi lưu lượng kết thúc, sau đó dừng phiên bản Snort. Bây giờ hãy phân tích tóm tắt đầu ra và trả lời câu hỏi.
`sudo ./traffic-generator.sh`

Bây giờ, bạn sẽ có các bản ghi trong thư mục hiện tại. Điều hướng đến thư mục " `145.254.160.237` ". Cổng nguồn nào được sử dụng để kết nối với cổng 53?
![alt text](<../png/Snort/snort-task6 (1).png>)

![alt text](<../png/Snort/snort-task6 (2).png>)

> ✅ **Đáp án:** `3009`

**Câu hỏi 2:** Đọc tệp snort.log bằng Snort; ID IP của gói tin thứ 10 là gì?

`snort -r snort.log.1640048004 -n 10`
![alt text](<../png/Snort/snort-task6 (3).png>)
> ✅ **Đáp án:** `49313`

**Câu hỏi 3:** Read the “snort.log.1640048004” file with Snort; what is the referer of the 4th packet?

`sudo snort -r snort.log.1640048004 -X -n 4`
![alt text](<../png/Snort/snort-task6 (4).png>)

**Câu hỏi 4:** Đọc tệp " snort.log.1640048004"  bằng Snort; số Ack của gói tin thứ 8 là bao nhiêu?
`sudo snort -r snort.log.1640048004 -n 8`
![alt text](<../png/Snort/snort-task6 (5).png>)

**Câu hỏi 5:** Read the “snort.log.1640048004” file with Snort; what is the number of the “TCP port 80” packets?
`sudo snort -r snort.log.1640048004 'tcp and port 80'`
![alt text](<../png/Snort/snort-task6 (6).png>)
