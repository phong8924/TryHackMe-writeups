## Các tham số phổ biến của công cụ `tshark`

| Parameter     | Mục đích |
|---------------|----------|
| `-h`          | Hiển thị trang trợ giúp với các tính năng phổ biến nhất. <br>Ví dụ: `tshark -h` |
| `-v`          | Hiển thị thông tin phiên bản. <br>Ví dụ: `tshark -v` |
| `-D`          | Liệt kê các giao diện có thể bắt gói tin. <br>Ví dụ: `tshark -D` |
| `-i`          | Chọn giao diện để bắt lưu lượng mạng trực tiếp. <br>Ví dụ: `tshark -i 1`, `tshark -i ens55` |
| *(Không tham số)* | Bắt lưu lượng giống như công cụ `tcpdump`. <br>Ví dụ: `tshark` |


## Các tham số mở rộng của công cụ `tshark`

| Parameter     | Mục đích |
|---------------|----------|
| `-r`          | Đọc/giao tiếp dữ liệu từ một tệp bắt gói tin. <br>Ví dụ: `tshark -r demo.pcapng` |
| `-c`          | Giới hạn số lượng gói tin sẽ được bắt/đọc. <br>Ví dụ: `tshark -c 10` (dừng sau khi xử lý 10 gói tin) |
| `-w`          | Ghi lưu lượng mạng vào tệp. <br>Ví dụ: `tshark -w sample-capture.pcap` |
| `-V`          | Chế độ chi tiết. <br>Hiển thị thông tin chi tiết cho từng gói tin, tương tự như khung "Packet Details" trong Wireshark. <br>Ví dụ: `tshark -V` |
| `-q`          | Chế độ im lặng. <br>Không hiển thị gói tin trên terminal. <br>Ví dụ: `tshark -q` |
| `-x`          | Hiển thị dữ liệu dạng hex và ASCII của từng gói tin. <br>Ví dụ: `tshark -x` |


## Các tham số điều kiện bắt gói trong `tshark`

Là một công cụ sniff và phân tích gói tin, `tshark` có thể được cấu hình để đếm gói tin và dừng ở một điều kiện cụ thể, hoặc chạy theo cấu trúc vòng lặp. Các tham số phổ biến như sau:

### Tham số `-a`: Xác định điều kiện dừng cho một lần chạy (Autostop)

| Parameter | Mục đích |
|-----------|----------|
| `-a duration:X` | Bắt lưu lượng và dừng sau **X giây**. <br>Ví dụ: `tshark -w test.pcap -a duration:1` |
| `-a filesize:X` | Dừng sau khi tệp bắt gói đạt **X KB**. <br>Ví dụ: `tshark -w test.pcap -a filesize:10` |
| `-a files:X`    | Dừng sau khi tạo **X tệp** đầu ra. <br>Ví dụ: `tshark -w test.pcap -a filesize:10 -a files:3` |

---

### Tham số `-b`: Kiểm soát buffer vòng lặp (vòng lặp vô hạn – Infinite Loop)

| Parameter | Mục đích |
|-----------|----------|
| `-b duration:X` | Bắt lưu lượng trong **X giây**, sau đó tạo tệp mới để ghi tiếp. <br>Ví dụ: `tshark -w test.pcap -b duration:1` |
| `-b filesize:X` | Sau khi tệp đạt **X KB**, tạo tệp mới để ghi tiếp. <br>Ví dụ: `tshark -w test.pcap -b filesize:10` |
| `-b files:X`    | Sau khi tạo **X tệp**, ghi đè lên tệp cũ nhất (vòng lặp tệp). <br>Ví dụ: `tshark -w test.pcap -b filesize:10 -b files:3` |


## Tham số lọc gói tin trong `tshark`: Lọc khi bắt và khi hiển thị

Trong `tshark`, có hai **giai đoạn lọc gói tin** chính:

- **Lọc khi bắt (Capture Filters):**  
  Áp dụng **trước khi bắt lưu lượng**, nhằm lưu lại **chỉ những phần cần thiết**. Đây là cách lọc gọn lưu lượng đầu vào để tránh lưu mọi thứ không cần thiết.  
  🔒 Không thể thay đổi trong quá trình bắt gói tin.

- **Lọc khi hiển thị (Display Filters):**  
  Áp dụng **sau khi bắt gói**, nhằm **phân tích và thu hẹp số gói tin hiển thị** để điều tra sâu hơn.  
  🔄 Có thể thay đổi linh hoạt trong quá trình phân tích.

> `tshark` hỗ trợ cả **Berkeley Packet Filters (BPF)** và **cú pháp lọc của Wireshark**, tương ứng với hai tham số chính bên dưới:

| Parameter | Mục đích |
|-----------|----------|
| `-f`      | **Capture filter**: Dùng để lọc gói tin ngay trong quá trình bắt. Cú pháp giống BPF hoặc bộ lọc bắt của Wireshark. <br>Ví dụ: `tshark -i eth0 -f "tcp port 80"` |
| `-Y`      | **Display filter**: Dùng để lọc gói tin khi hiển thị/đọc file. Cú pháp giống bộ lọc hiển thị của Wireshark. <br>Ví dụ: `tshark -r file.pcap -Y "http.request"` |

---

### 🔍 So sánh nhanh: Capture vs Display Filters

| Đặc điểm           | Capture Filter (`-f`)                    | Display Filter (`-Y`)                     |
|--------------------|-------------------------------------------|-------------------------------------------|
| Thời điểm áp dụng  | Trước khi bắt gói                        | Sau khi đã bắt gói                        |
| Mục tiêu           | Giảm kích thước file, lọc lưu lượng gốc  | Điều tra sâu, hiển thị thông tin cụ thể  |
| Thay đổi linh hoạt | ❌ Không                                 | ✅ Có thể thay đổi khi phân tích         |
| Cú pháp            | BPF (Berkeley Packet Filter)             | Wireshark filter syntax                   |




## Các thành phần định tính (Qualifier) trong Capture Filters

Trong bộ lọc bắt gói (`-f`), bạn có thể sử dụng các **qualifier** để xác định loại mục tiêu, hướng và giao thức cần lọc. Nếu không chỉ định rõ, `tshark` sẽ sử dụng mặc định là `host`.

---

### 1. Type – Loại mục tiêu lọc

| Tùy chọn     | Mô tả                             | Ví dụ |
|--------------|-----------------------------------|-------|
| `host`       | Lọc theo địa chỉ IP cụ thể        | `tshark -f "host 10.10.10.10"` |
| `net`        | Lọc theo dải mạng                 | `tshark -f "net 10.10.10.0/24"` |
| `port`       | Lọc theo một cổng cụ thể          | `tshark -f "port 80"` |
| `portrange`  | Lọc theo dải cổng                 | `tshark -f "portrange 80-100"` |

> Nếu không chỉ rõ loại (`host`, `net`, v.v.), mặc định `host` sẽ được sử dụng.

---

### 2. Direction – Hướng gói tin

| Tùy chọn | Mô tả                                 | Ví dụ |
|----------|----------------------------------------|-------|
| `src`    | Lọc theo địa chỉ nguồn                 | `tshark -f "src host 10.10.10.10"` |
| `dst`    | Lọc theo địa chỉ đích                  | `tshark -f "dst host 10.10.10.10"` |

> Nếu không chỉ định hướng, mặc định sẽ là cả hai chiều (`src or dst`).

---

### 3. Protocol – Giao thức mạng

Bạn có thể lọc theo các giao thức mạng phổ biến hoặc sử dụng số giao thức do IANA gán.

| Giao thức     | Mô tả                               | Ví dụ |
|---------------|--------------------------------------|-------|
| `tcp`         | Lọc gói TCP                         | `tshark -f "tcp"` |
| `udp`         | Lọc gói UDP                         | `tshark -f "udp"` |
| `icmp`        | Lọc gói ICMP                        | `tshark -f "icmp"` |
| `ip`          | Lọc tất cả gói IP                   | `tshark -f "ip"` |
| `ip6`         | Lọc gói IPv6                        | `tshark -f "ip6"` |
| `arp`         | Lọc gói ARP                         | `tshark -f "arp"` |
| `ether`       | Lọc theo địa chỉ MAC                | `tshark -f "ether host F8:DB:C5:A2:5D:81"` |
| `ip proto X`  | Lọc theo mã số giao thức IP (IANA) | `tshark -f "ip proto 1"` (ICMP) |

---

> 📌 **Ghi chú:**  
> - Bộ lọc dạng capture sử dụng cú pháp **BPF** (Berkeley Packet Filter).  
> - Chúng hoạt động **trước khi gói tin được ghi vào file**, do đó tiết kiệm tài nguyên và dung lượng.

