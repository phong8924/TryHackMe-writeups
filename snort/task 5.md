
# Task 5 - Snort: Sniffer Mode

Snort có thể chạy ở chế độ Sniffer giống như `tcpdump`, sử dụng các tham số dòng lệnh để hiển thị thông tin gói tin theo các mức độ chi tiết khác nhau.

## Các Tham Số Sniffer Mode

| Tham số | Mô tả |
|---------|------|
| `-v`    | Verbose - Hiển thị chi tiết TCP/IP trong console |
| `-d`    | Hiển thị payload (dữ liệu) của gói tin |
| `-e`    | Hiển thị header lớp liên kết (Ethernet, TCP/IP, UDP, ICMP) |
| `-X`    | Hiển thị toàn bộ nội dung gói tin ở định dạng HEX |
| `-i`    | Chọn giao diện mạng để sniff, ví dụ: `eth0` |

## Cách sử dụng từng tham số

### 1. `-i`: Chọn giao diện mạng

```bash
sudo snort -v -i eth0
```

Nếu chỉ có một giao diện, Snort sẽ tự động sử dụng nó.

---

### 2. `-v`: Verbose Mode

```bash
sudo snort -v
```

Hiển thị thông tin giống như `tcpdump`, ví dụ:

```
192.168.175.129:34316 -> 192.168.175.2:53
UDP TTL:64 TOS:0x0 ID:23826 IpLen:20 DgmLen:64 DF
```

---

### 3. `-d`: Hiển thị dữ liệu payload

```bash
sudo snort -d
```

Hiển thị dữ liệu dạng ASCII trong phần payload:

```
99 A5 01 00 00 01 00 00 ... google.com ...
```

---

### 4. `-de`: Payload + Link-layer headers

```bash
sudo snort -de
```

Hiển thị cả địa chỉ MAC và payload:

```
00:0C:29:A5:B7:A2 -> 00:50:56:E1:9B:9D type:0x800 len:0x46
... google.com ...
```

---

### 5. `-X`: Hiển thị toàn bộ gói tin ở HEX

```bash
sudo snort -X
```

Hiển thị gói tin đầy đủ theo dạng HEX + ASCII:

```
0x0000: 01 00 5E 7F FF FA 00 50 ...
...
0x0060: 36 37
```

---

## Kết hợp nhiều tham số

Snort hỗ trợ dùng kết hợp tham số:

- `snort -v`
- `snort -vd`
- `snort -de`
- `snort -v -d -e`
- `snort -X`
