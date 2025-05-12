
# Snort in IDS/IPS Mode

Snort có thể hoạt động ngoài chức năng đánh hơi và ghi nhật ký cơ bản — nó còn hoạt động như một Hệ thống phát hiện và ngăn chặn xâm nhập (IDS/IPS) bằng cách sử dụng các quy tắc do người dùng xác định.

## Key Parameters for IDS/IPS Mode

| Parameter | Description |
|-----------|-------------|
| `-c`      | Chỉ định tập tin cấu hình |
| `-T`      | Kiểm tra tập tin cấu hình |
| `-N`      | Vô hiệu hóa ghi nhật ký |
| `-D`      | Run in background (daemon) mode |
| `-A`      | Set alert mode (`full`, `fast`, `console`, `cmg`, `none`) |

> **Quy tắc cảnh báo được sử dụng trong các ví dụ:** 
> `alert icmp any any <> any any (msg: "ICMP Packet Found"; sid: 100001; rev:1;)`  
> Located in: `/etc/snort/rules/local.rules`

---

## Modes and Examples

### 1. Test Configuration
```bash
sudo snort -c /etc/snort/snort.conf -T
```

### 2. Disable Logging
```bash
sudo snort -c /etc/snort/snort.conf -N
```

### 3. Background Mode (Daemon)
```bash
sudo snort -c /etc/snort/snort.conf -D
ps -ef | grep snort
sudo kill -9 <PID>
```

### 4. Alert Modes

- **Console**
```bash
sudo snort -c /etc/snort/snort.conf -A console
```
- **CMG (with hex/text payload)**
```bash
sudo snort -c /etc/snort/snort.conf -A cmg
```
- **Fast (summary format in log)**
```bash
sudo snort -c /etc/snort/snort.conf -A fast
```
- **Full (detailed log information)**
```bash
sudo snort -c /etc/snort/snort.conf -A full
```
- **None (disables alerting, logs in binary format)**
```bash
sudo snort -c /etc/snort/snort.conf -A none
```

### 5. Run with Rule File Only (No Config)
```bash
sudo snort -c /etc/snort/rules/local.rules -A console
```

---

## Notes

- Lưu lượng truy cập phải hoạt động để Snort hoạt động — sử dụng tập lệnh tạo lưu lượng truy cập.
- Một số chế độ cảnh báo không hiển thị đầu ra trên bảng điều khiển (ví dụ: `fast`, `full`, `none`) — hãy kiểm tra nhật ký thay thế.
- Chế độ nền (`-D`) hữu ích cho tự động hóa nhưng nên được sử dụng với cấu hình ổn định.

---

>**Câu hỏi** Kiểm tra lưu lượng truy cập bằng tệp cấu hình mặc định.

`sudo snort -c /etc/snort/snort.conf -A full -l .`

>Thực thi tập lệnh tạo lưu lượng và chọn "TASK-7 Exercise" . Đợi cho đến khi lưu lượng dừng lại, sau đó dừng phiên bản Snort. Bây giờ hãy phân tích tóm tắt đầu ra và trả lời câu hỏi.

`sudo ./traffic-generator.sh`

>Số lượng phương thức HTTP GET được phát hiện là bao nhiêu?
png/snort-task7 (1).png
